---
title: "实现旧语言 Service2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24e847eb0f1d05717ab6b114921a66b04cd94922
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-legacy-language-service"></a>实现旧语言服务
若要实现使用托管的包框架 (MPF) 的语言服务，你必须从派生类<xref:Microsoft.VisualStudio.Package.LanguageService>类，实现以下抽象方法和属性：  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 属性  
  
 实现这些方法和属性，请参阅下面有关详细信息的相应部分。  
  
 若要支持其他功能，你的语言服务可能需要从 MPF 语言服务类; 之一中派生一个类例如，若要支持其他菜单命令，你必须从派生类<xref:Microsoft.VisualStudio.Package.ViewFilter>类并重写命令处理方法的几个 (请参阅<xref:Microsoft.VisualStudio.Package.ViewFilter>有关详细信息)。 <xref:Microsoft.VisualStudio.Package.LanguageService>类提供了大量的调用来创建的各个类的新实例的方法，并且您重写适当的创建方法以提供您的类的实例。 例如，你需要重写<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类以返回你自己的实例<xref:Microsoft.VisualStudio.Package.ViewFilter>类。 请参阅有关详细信息的"实例化自定义类"一节。  
  
 语言服务还可以提供其自己的图标，在多个位置中使用。 例如，当 IntelliSense 完成列表显示时，列表中的每个项可以有与之关联，将项标记为方法、 类、 命名空间和属性，一个图标或的任何需要你的语言。 使用这些图标中所有的 IntelliSense 列表**导航栏**，然后在**错误列表**任务窗口。 请参阅下面有关详细信息的"语言服务映像"部分。  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences 方法  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法始终返回同一个实例<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。 可以使用基本<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类如果不需要你语言服务的任何其他首选项。 MPF 语言服务类假定存在至少基<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。  
  
### <a name="example"></a>示例  
 此示例演示的典型实现<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法。 此示例使用基本<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>GetScanner 方法  
 此方法返回的实例<xref:Microsoft.VisualStudio.Package.IScanner>实现面向行的分析器或用于获取令牌及其类型和触发器的扫描程序的对象。 此扫描程序中使用<xref:Microsoft.VisualStudio.Package.Colorizer>尽管扫描程序还可用于获取令牌的类型和触发器以更复杂的分析操作作类着色。 必须提供实现的类<xref:Microsoft.VisualStudio.Package.IScanner>接口，并且您必须在实现所有方法<xref:Microsoft.VisualStudio.Package.IScanner>接口。  
  
### <a name="example"></a>示例  
 此示例演示的典型实现<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法。 `TestScanner`类实现<xref:Microsoft.VisualStudio.Package.IScanner>（未显示） 的接口。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>ParseSource 方法  
 分析基于多种不同原因导致的源文件。 此方法有<xref:Microsoft.VisualStudio.Package.ParseRequest>对象，描述与特定分析操作的预期。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法调用的更复杂的分析器，确定令牌功能和作用域。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法用在支持的智能感知操作以及大括号匹配。 即使不支持此类高级的操作，您仍必须返回有效<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象，并且需要创建一个类以实现<xref:Microsoft.VisualStudio.Package.AuthoringScope>接口，并在该接口上实现所有方法。 你可以从所有方法返回 null 值但<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象本身必须不能为 null 值。  
  
### <a name="example"></a>示例  
 此示例演示的一个最小实现<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法和<xref:Microsoft.VisualStudio.Package.AuthoringScope>类，不足以允许语言服务，若要编译并不实际支持更高级的任何的功能情况下正常工作。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Name 属性  
 此属性返回语言服务的名称。 这必须是该语言服务已注册时指定的相同名称。 此名称用于在多个位置中，最明显的是<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类的名称用于访问注册表。 返回此属性的名称必须不会本地化，因为它将用于在注册表中注册表项与键的名称。  
  
### <a name="example"></a>示例  
 此示例演示一种可能的实现<xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>属性。 请注意，此处的名称是硬编码： 的实际名称应获得从资源文件，因此可在注册语言服务 (请参阅[注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md))。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>实例化自定义类  
 可以重写中指定的类的以下方法以提供您自己版本的每个类的实例。  
  
### <a name="in-the-languageservice-class"></a>在 LanguageService 类  
  
|方法|返回的类|描述|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|若要支持自定义添加到文本视图。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|若要支持自定义文档属性。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|若要支持**导航栏**。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|若要在代码段模板中支持的功能。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|若要支持 （此方法通常未重写） 的代码段。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|若要支持的自定义<xref:Microsoft.VisualStudio.Package.ParseRequest>（此方法通常未重写） 的结构。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|若要支持指定注释字符和自定义方法签名的格式设置源代码。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|若要支持其他菜单命令。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|若要支持语法突出显示 （此方法通常未重写）。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|若要支持对语言首选项的访问。 此方法必须实现，但可以返回的基类的实例。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|若要提供用于将标识在行上的标记的类型的分析器。 必须实现此方法和<xref:Microsoft.VisualStudio.Package.IScanner>必须派生自。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|提供用于标识功能以及整个源文件范围内的分析器。 此方法必须实施，并且必须返回的版本的实例<xref:Microsoft.VisualStudio.Package.AuthoringScope>类。 如果所有你想要支持语法突出显示 (这需要<xref:Microsoft.VisualStudio.Package.IScanner>从返回的分析器<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法)，则可以执行任何操作不返回此方法中的版本<xref:Microsoft.VisualStudio.Package.AuthoringScope>其方法都将返回 null 值的类。|  
  
### <a name="in-the-source-class"></a>在源类  
  
|方法|返回的类|描述|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|用于自定义 IntelliSense 完成列表 （此方法通常未重写） 的显示。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|在错误列表任务列表; 支持标记具体而言，支持打开文件并跳转到引起错误的行之外的功能。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|用于自定义 IntelliSense 参数信息工具提示的显示。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|支持注释的代码。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|用于收集在分析操作过程中的信息。|  
  
### <a name="in-the-authoringscope-class"></a>在 AuthoringScope 类  
  
|方法|返回的类|描述|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|提供声明，例如成员或类型的列表。 此方法必须实现，但可以返回一个 null 值。 如果此方法返回有效的对象，该对象必须是你的版本的实例<xref:Microsoft.VisualStudio.Package.Declarations>类。|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|提供有关给定上下文方法签名的列表。 此方法必须实现，但可以返回一个 null 值。 如果此方法返回有效的对象，该对象必须是你的版本的实例<xref:Microsoft.VisualStudio.Package.Methods>类。|  
  
## <a name="language-service-images"></a>语言服务映像  
 若要提供用于在整个语言服务的图标列表，重写<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类，并返回<xref:System.Windows.Forms.ImageList>包含图标。 基<xref:Microsoft.VisualStudio.Package.LanguageService>类加载一组默认的图标。 由于在这些需要图标的位置，则指定完全相同的映像索引，你自己的映像列表的排列方式是完全取决于你。  
  
### <a name="images-used-in-intellisense-completion-lists"></a>在 IntelliSense 完成列表中使用的图像  
 对于 IntelliSense 完成列表的图像索引指定中每个项<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>方法<xref:Microsoft.VisualStudio.Package.Declarations>类，如果你想要提供一个图像索引时，必须重写。 从返回的值<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>方法是提供给的图像列表索引<xref:Microsoft.VisualStudio.Package.CompletionSet>类构造函数和相同的图像列表，它是从返回<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类 （你可以更改到的图像列表用于<xref:Microsoft.VisualStudio.Package.CompletionSet>如果重写<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>中的方法<xref:Microsoft.VisualStudio.Package.Source>类提供一个不同的图像列表)。  
  
### <a name="images-used-in-the-navigation-bar"></a>在导航栏中使用的图像  
 **导航栏**显示类型和成员的列表，并使用快速导航可以显示图标。 从获取这些图标<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类并不能重写专门为**导航栏**。 用于组合框中的每个项的索引填充的列表，表示组合框时指定<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>中的方法<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>类 (请参阅[旧语言服务中的导航栏的支持](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). 这些映像索引从分析器，通常通过你的版本以某种方式获取<xref:Microsoft.VisualStudio.Package.Declarations>类。 获取索引的方式是完全取决于你。  
  
### <a name="images-used-in-the-error-list-task-window"></a>在错误列表任务窗口中使用的图像  
 每当<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法分析器 (请参阅[旧语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) 遇到错误，并将传递到该错误<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>中的方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>类，在中报告错误**错误列表**任务窗口。 图标可以显示在任务窗口中每个项与相关联，该图标来自同一图像列表从返回<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。 MPF 类的默认行为是不会显示错误消息的映像。 但是，通过派生类中的重写此行为<xref:Microsoft.VisualStudio.Package.Source>类并重写<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>方法。 在该方法中，你创建一个新<xref:Microsoft.VisualStudio.Package.DocumentTask>对象。 再返回该对象，可以使用<xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A>属性<xref:Microsoft.VisualStudio.Package.DocumentTask>要设置的图像索引对象。 它看起来应类似下面的示例。 请注意，`TestIconImageIndex`是一个枚举，列出所有图标和特定于此示例。 你可能有不同方式来标识语言服务中的图标。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TastPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>语言服务默认图像列表  
 随附的基的 MPF 语言服务类的默认图像列表包含大量的更常见的语言元素与关联的图标。 这些图标大量排列分批六个变体，对应的公共、 内部、 友元，受保护、 私有的和快捷方式访问概念。 例如，你可以根据是否公共、 受保护或私有方法不同的图标。  
  
 以下枚举指定的每个图标集的典型名称，并指定相关联的索引。 例如，基于枚举，你可以指定为受保护方法的图像索引`(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`。 你可以更改为所需的此枚举中的名称。  
  
```csharp  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>另请参阅  
 [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [旧语言服务概述](../../extensibility/internals/legacy-language-service-overview.md)   
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [旧版语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)