---
title: "实现传统语言服务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "实现语言服务 [托管的包框架]"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 实现传统语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用托管包结构，若要实现语言服务 \(MPF\)，必须从 <xref:Microsoft.VisualStudio.Package.LanguageService> 类派生类并实现下列抽象方法和属性:  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 属性  
  
 请参见下面相应节有关实现这些方法和属性的详细信息。  
  
 若要支持附加功能，语言服务可能必须从某个 MPF 语言服务类派生类;例如，支持其他的菜单命令，必须从 <xref:Microsoft.VisualStudio.Package.ViewFilter> 类派生类并重写处理方法的多个命令 \(请参见 <xref:Microsoft.VisualStudio.Package.ViewFilter> 有关详细信息\)。  <xref:Microsoft.VisualStudio.Package.LanguageService> 类提供调用创建各类的新实例的方法，并重写相应的创建方法提供类的实例。  例如，则需要重写在 <xref:Microsoft.VisualStudio.Package.LanguageService> 类的 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> 方法返回实例拥有 <xref:Microsoft.VisualStudio.Package.ViewFilter> 类。  有关更多详细信息参见 “实例化的自定义类”一节。  
  
 语言服务也可以提供自己的图标，用于多个地方。  例如，在中，当 IntelliSense 完成列表时显示列表中，每个项目中具有与其关联的图标，标记该项作为方法，类，命名空间，属性，或者操作的该语言是必需的。  这些图标用于所有 IntelliSense 列表， **导航栏**，然后在 **错误表** 任务。  请参见下面的 “语言服务 image”部分有关详细信息。  
  
## GetLanguagePreferences 方法  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法始终返回 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类的同一个实例。  ，如果不需要语言服务，的任何其他的喜好您可以使用基本 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。  MPF 语言服务类假定有基本 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类出现。  
  
### 示例  
 此示例演示 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法的一个典型的实现。  此示例使用基本 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。  
  
```c#  
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
  
## GetScanner 方法  
 此方法返回 <xref:Microsoft.VisualStudio.Package.IScanner> 对象的实例实现一个 \(可沿的分析器或扫描仪提供用于获取标记使用了及其类型和触发器。  此扫描仪用于 <xref:Microsoft.VisualStudio.Package.Colorizer> 类进行着色，虽然扫描仪能用于获取标记类型和触发器也用作对于更复杂的分析操作中的一个前奏。  必须提供实现 <xref:Microsoft.VisualStudio.Package.IScanner> 接口的类，并且您必须在 <xref:Microsoft.VisualStudio.Package.IScanner> 接口的所有方法。  
  
### 示例  
 此示例演示 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法的一个典型的实现。  `TestScanner` 类实现 <xref:Microsoft.VisualStudio.Package.IScanner> 接口 \(未显示\)。  
  
```c#  
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
  
## ParseSource 方法  
 分析基于多种不同的原因的源文件。  提供描述此方法的一 <xref:Microsoft.VisualStudio.Package.ParseRequest> 对象所需的特定分析操作。  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 调用方法确定标记功能和大小的更复杂的分析器。  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法以支持 IntelliSense 操作以及括号匹配使用。  即使不支持这些高级操作，您还必须返回了有效的 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 对象，并要求您创建实现 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 接口的类并执行该接口的所有方法。  可以返回来自任何方法的 null 值，但 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 对象不能为 null 值。  
  
### 示例  
 此示例演示 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法和 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 类的一个最小实现，满足允许语言服务生成并运行，而不会实际支持任何高级功能。  
  
```c#  
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
  
## name 属性  
 此属性返回语言服务的名称。  ，当语言服务注册，则必须是命名的相同的名称。  此名称用于许多的地方，最重要的是该名称用于访问注册表的 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。  此属性返回的名称，如果在注册表中的注册表项和名称，不能本地化。  
  
### 示例  
 此示例演示 <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 属性的一个可能的实现。  请注意此时该名称硬编码:应从资源文件中获取的实际名称，因此可用于注册语言服务 \(请参见 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)\)。  
  
```c#  
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
  
## 实例化的自定义类  
 在指定的类的以下方法可以重写提供实例拥有每个类的版本。  
  
### 在 LanguageService 类  
  
|方法|返回的类|说明|  
|--------|----------|--------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|支持自定义添加到文本视图。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|若要支持自定义文档属性。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|支持 **导航栏**。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|支持在代码段模板中的功能。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|支持代码段 \(此方法通常不重写\)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|支持 <xref:Microsoft.VisualStudio.Package.ParseRequest> 结构的自定义 \(此方法通常不重写\)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|支持格式化源代码，指定注释字符和自定义方法签名。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|支持其他的菜单命令。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|支持语法显示 \(此方法通常不重写\)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|支持对语言首选项的访问。  必须执行此方法，但可能返回基类的实例。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|提供用于标识标记的类型的分析器中的行。  必须执行此方法，并且必须派生自。 <xref:Microsoft.VisualStudio.Package.IScanner>|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|提供用于标识功能和大小使用的分析器在整个源文件中。  必须执行此方法并且必须返回 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 类版本的实例。  如果要支持的所有没有为显示的语法 \(需要从 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法返回的 <xref:Microsoft.VisualStudio.Package.IScanner> 分析器\)，您可以执行此方法不返回方法都返回空值 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 类的版本。|  
  
### 在源类  
  
|方法|返回的类|说明|  
|--------|----------|--------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|为自定义 IntelliSense 显示完成列表 \(此方法通常不重写\)。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|对于支持中的标记错误表任务列表;具体而言，在打开文件并跳转的功能支持到导致此错误的行之外。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|为自定义 IntelliSense 参数信息显示工具提示。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|为支持注释的代码。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|为收集信息在分析操作时。|  
  
### 在 AuthoringScope 类  
  
|方法|返回的类|说明|  
|--------|----------|--------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|提供列表的说明 \(如成员或类型。  必须执行此方法，但可能返回空值。  如果此方法返回一个有效的对象，该对象必须是 <xref:Microsoft.VisualStudio.Package.Declarations> 类版本的实例。|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|为给定上下文提供方法签名列表。  必须执行此方法，但可能返回空值。  如果此方法返回一个有效的对象，该对象必须是 <xref:Microsoft.VisualStudio.Package.Methods> 类版本的实例。|  
  
## 语言服务图像  
 若要提供要使用的图标列表。语言服务，请重写在 <xref:Microsoft.VisualStudio.Package.LanguageService> 类的 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 方法并返回包含该图标的 <xref:System.Windows.Forms.ImageList> 。  默认设置图标的基本 <xref:Microsoft.VisualStudio.Package.LanguageService> 类加载。  因为在需要图标的那些具有指定确切的图像索引，您如何使请拥有图像列表完全由您决定。  
  
### 在 IntelliSense 完成的图像列表  
 向 IntelliSense 完成列表，图像索引来指定每个项目在 <xref:Microsoft.VisualStudio.Package.Declarations> 类的 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 方法，则必须重写，如果您希望提供图像索引。  从 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 方法返回的值是索引到图像列表提供给 <xref:Microsoft.VisualStudio.Package.CompletionSet> 类构造函数，并且这是同一图像列表返回从在 <xref:Microsoft.VisualStudio.Package.LanguageService> 类 \(图像列表 <xref:Microsoft.VisualStudio.Package.CompletionSet> 使用的 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 方法可以更改，如果重写在 <xref:Microsoft.VisualStudio.Package.Source> 类的 <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> 方法提供一个不同的图像列表\)。  
  
### 用于导航栏的图像  
 **导航栏** 显示列表类型和成员和进行快速导航使用可以显示图标。  这些图标从在 <xref:Microsoft.VisualStudio.Package.LanguageService> 类的 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 方法获取，并且不能用于 **导航栏**专门重写。  用于每一项的索引在组合框中指定，当列表表示组合框填充 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 类中的 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 方法 \(请参见 [对旧语言服务中的导航栏的支持](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)\)。  这些图像索引从分析器以某种方式获取，通常通过 <xref:Microsoft.VisualStudio.Package.Declarations> 类的版本。  索引如何获取完全由您决定。  
  
### 使用的图像错误表任务 " 窗口  
 每当 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法分析程序 \(请参见\) [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)遇到对 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> 方法的错误。 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 类，该错误。 **错误表** 任务 " 窗口报告的错误并将。  图标可以与显示在任务窗口和图标来自同一个图像列表返回从在 <xref:Microsoft.VisualStudio.Package.LanguageService> 类的 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 方案中的每个项目。  MPF 类的默认行为是不显示一条错误消息的图像。  但是，您可以通过派生类从 <xref:Microsoft.VisualStudio.Package.Source> 类并重写 <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> 方法重写此行为。  该方法，请创建一个新的 <xref:Microsoft.VisualStudio.Package.DocumentTask> 对象。  在返回该对象之前，可以使用在 <xref:Microsoft.VisualStudio.Package.DocumentTask> 对象的 <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> 属性设置图像索引。  这看起来类似于下面的示例。  请注意 `TestIconImageIndex` 是列出所有图标的枚举和特定于此示例。  在语言服务中具有标识图标不同的方式。  
  
```c#  
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
  
## 默认图像。语言服务列表  
 默认图像列表提供了类包含多种关联的图标与公共语言元素的基础 MPF 语言服务。  将大多数这些图标设置六个变体，使用公钥，内部， friends，保护，专用和快捷适当的访问概念。  例如，可以使用方法的不同图标基于它是否是公共的，从而保护或保密。  
  
 以下枚举提供设置的每个图标指定典型的名称并指定关联的索引。  例如，基于枚举，可以为一个受保护的方法指定图像索引用作 `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`。  可以更改此枚举的名称按照需要。  
  
```c#  
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
  
## 请参阅  
 [实现传统语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [旧的语言服务概述](../../extensibility/internals/legacy-language-service-overview.md)   
 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)