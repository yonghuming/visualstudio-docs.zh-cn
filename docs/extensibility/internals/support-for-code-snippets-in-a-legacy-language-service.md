---
title: "对旧语言服务中的代码段支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0089e5a8bf85ba352788767c821d95f41ca60eec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>对旧语言服务中的代码段的支持
代码片段是代码的一种插入到的源文件。 本身的代码片段是一组字段的基于 XML 的模板。 代码段插入，并且可以具有不同的值，具体取决于在插入代码段的上下文之后，将突出显示这些字段。 立即插入代码段后，该语言服务即可格式化代码段。  
  
 在一种特殊的编辑模式，允许的代码段以通过使用 TAB 键导航的字段中插入代码段。 字段可以支持 IntelliSense 样式下拉菜单。 用户通过键入 ENTER 或 ESC 键提交到源文件的代码段。 若要了解有关代码段的详细信息，请参阅[代码段](../../ide/code-snippets.md)。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解详细信息，请参阅[演练： 实现代码段](../../extensibility/walkthrough-implementing-code-snippets.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>托管包框架支持的代码段  
 托管的包框架 (MPF) 支持大多数代码段功能，从读取插入代码段的模板，启用这两个特殊编辑模式。 通过管理支持<xref:Microsoft.VisualStudio.Package.ExpansionProvider>类。  
  
 当<xref:Microsoft.VisualStudio.Package.Source>实例化类时，<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类调用以获取<xref:Microsoft.VisualStudio.Package.ExpansionProvider>对象 (请注意，基<xref:Microsoft.VisualStudio.Package.LanguageService>类始终返回一个新<xref:Microsoft.VisualStudio.Package.ExpansionProvider>每个对象<xref:Microsoft.VisualStudio.Package.Source>对象的名称。  
  
 MPF 不支持扩展函数。 扩展函数是命名的函数，嵌入代码段模板，并返回一个或多个要放置在一个字段的值。 将值返回由语言服务本身通过<xref:Microsoft.VisualStudio.Package.ExpansionFunction>对象。 <xref:Microsoft.VisualStudio.Package.ExpansionFunction>对象必须由语言服务，以支持扩展函数实现。  
  
## <a name="providing-support-for-code-snippets"></a>提供有关代码段的支持  
 若要启用对代码段支持，你必须提供，或安装代码片段，你必须提供要插入这些代码段的用户的方法。 有三个步骤启用对代码段的支持：  
  
1.  安装代码段文件。  
  
2.  启用语言服务的代码段。  
  
3.  调用<xref:Microsoft.VisualStudio.Package.ExpansionProvider>对象。  
  
### <a name="installing-the-snippet-files"></a>安装代码段文件  
 一种语言的所有代码段存储为 XML 文件中的模板通常代码段模板每个文件。 有关代码段模板使用的 XML 架构的详细信息，请参阅[代码片段架构参考](../../ide/code-snippets-schema-reference.md)。 每个代码段模板标识与语言 id。 这种语言 ID 在注册表中指定和放入`Language`属性\<代码 > 模板中的标记。  
  
 通常有两个代码段模板文件的存储位置的位置： 1） 的位置安装你的语言以及 2） 在用户的文件夹。 这些位置添加到注册表因此，Visual Studio**代码片段管理器**可以找到这些代码段。 用户的文件夹是由用户创建的代码段的存储位置。  
  
 已安装的代码段模板文件的典型文件夹布局如下所示： *[InstallRoot]*\\*[TestLanguage]*\Snippets\\*[LCID]*\Snippets。  
  
 *[InstallRoot]*是你的语言安装中的文件夹。  
  
 *[TestLanguage]*是你作为文件夹名称的语言的名称。  
  
 *[LCID]*是区域设置 id。 这是你的代码段的如何本地化的版本存储。 例如，英语的区域设置 ID 为 1033，因此*[LCID]*替换为 1033年。  
  
 必须提供一个附加的文件，并且是索引文件，通常称为 SnippetsIndex.xml 或 ExpansionsIndex.xml （你可以使用任何有效的文件名以.xml）。 此文件通常存储在*[InstallRoot]*\\*[TestLanguage]*文件夹，并指定 snippets 文件夹，以及语言 ID 的确切位置和 GUID 的语言使用这些代码段的服务。 在"安装注册表项"的后面部分所述的索引文件的准确路径被置于注册表。 下面是 SnippetsIndex.xml 文件的示例：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 \<语言 > 标记指定的语言 ID (`Lang`属性) 和语言服务 GUID。  
  
 此示例假定你已在 Visual Studio 安装文件夹安装语言服务。 %LCID%将被替换为用户的当前区域设置 id。 多个\<SnippetDir > 标记可以添加，一个用于每个不同的目录和区域设置。 此外，代码段文件夹可以包含子文件夹，其中每个索引文件中标识\<SnippetSubDir > 标记嵌入在\<SnippetDir > 标记。  
  
 用户还可以创建你的语言自己段。 这些通常存储在用户的设置文件夹中，例如*[TestDocs]*\Code 代码段\\*[TestLanguage]*\Test 代码段，其中*[TestDocs]*是 Visual Studio 的用户的设置文件夹的位置。  
  
 以下的替换元素可以放在路径存储在\<DirPath > 标记中的索引文件。  
  
|元素|描述|  
|-------------|-----------------|  
|%LCID%|区域设置 id。|  
|%Installroot%|Visual Studio 中，例如，C:\Program Files\Microsoft Visual Studio 8 的根安装文件夹。|  
|%Projdir%|包含当前项目文件夹。|  
|%Projitem%|包含当前的项目项的文件夹。|  
|%Testdocs%|用户的设置文件夹，例如，C:\Documents and Settings 文件夹中\\*[username]*documents\visual Studio\8。|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>启用语言服务的代码段  
 你可以启用代码段语言服务的添加<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>属性设为你的 VSPackage (请参阅[注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)有关详细信息)。 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>和<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A>参数是可选的但应包括`SearchPaths`命名参数，以便通知**代码片段管理器**你的代码段的位置。  
  
 下面是如何使用此特性的示例：  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>调用扩展提供程序  
 语言服务控制插入的任何代码段，以及调用插入的方式。  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>调用代码段的扩展提供程序  
 有两种方法来调用扩展提供程序： 通过使用菜单命令或通过从完成列表的快捷方式。  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>通过使用菜单命令将插入代码段  
 若要使用菜单命令显示代码段浏览器，你可以添加菜单命令，然后调用<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>中的方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider>到该菜单命令的响应中的接口。  
  
1.  添加到.vsct 文件的命令和一个按钮。 你可以找到因此在执行操作的说明[使用菜单命令创建扩展](../../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  从派生类<xref:Microsoft.VisualStudio.Package.ViewFilter>类并重写<xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A>方法，以指示新的菜单命令的支持。 此示例将始终启用菜单命令。  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  重写<xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A>中的方法<xref:Microsoft.VisualStudio.Package.ViewFilter>类来获取<xref:Microsoft.VisualStudio.Package.ExpansionProvider>对象并调用<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>对该对象的方法。  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     中的以下方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider>类由 Visual Studio 中的给定的顺序在过程中调用的插入代码段：  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     后<xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>方法调用，在插入代码段和<xref:Microsoft.VisualStudio.Package.ExpansionProvider>对象处于一种特殊的编辑模式，用于修改刚插入代码段。  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>通过使用快捷方式插入代码片段。  
 实现从完成列表的快捷方式是而不是实现菜单命令的复杂得多。 首先，你必须将代码段快捷方式添加到 IntelliSense 文字自动完成列表中。 然后必须时已完成由于插入代码段快捷名称进行检测。 最后，你必须获得的代码段的标题和路径使用快捷名称，并传递到该信息<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider>方法。  
  
 若要添加到 word 完成列表的代码段快捷方式，将其添加到<xref:Microsoft.VisualStudio.Package.Declarations>对象中你<xref:Microsoft.VisualStudio.Package.AuthoringScope>类。 你必须确保你可以标识作为代码段名称的快捷方式。 有关示例，请参阅[演练： 获取列表的安装代码片段 （旧实现）](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
 你可以检测中的代码段快捷方式插入<xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A>方法<xref:Microsoft.VisualStudio.Package.Declarations>类。 代码段名称已插入到的源文件，因为必须先删除时插入扩展。 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>方法采用一个描述代码段的插入点的范围; 如果源文件中，范围包括整个代码段名称，该名称将被替换的片段。  
  
 以下是的版本<xref:Microsoft.VisualStudio.Package.Declarations>处理给定快捷名称的代码段插入的类。 中的其他方法<xref:Microsoft.VisualStudio.Package.Declarations>为清楚起见省略了类。 请注意，此类的构造函数采用<xref:Microsoft.VisualStudio.Package.LanguageService>对象。 这可以从自己版本的传入<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象 (例如，你实现<xref:Microsoft.VisualStudio.Package.AuthoringScope>类可能需要<xref:Microsoft.VisualStudio.Package.LanguageService>对象在其构造函数并将传递到该对象你`TestDeclarations`类构造函数)。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 当语言服务获取的快捷名称时，它将调用<xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A>方法来获取文件名和代码段的标题。 语言服务然后调用<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>中的方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider>类，以插入代码段。 在给定的顺序调用下列方法由 Visual Studio<xref:Microsoft.VisualStudio.Package.ExpansionProvider>在过程中插入代码段的类：  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 语言服务获取已安装的代码代码段的列表的详细信息，请参阅[演练： 获取列表的安装代码片段 （旧实现）](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
## <a name="implementing-the-expansionfunction-class"></a>实现 ExpansionFunction 类  
 扩展函数是命名的函数，嵌入代码段模板，并返回一个或多个要放置在一个字段的值。 为了支持扩展函数语言服务中，你必须从派生类<xref:Microsoft.VisualStudio.Package.ExpansionFunction>类，实现<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>方法。 然后，你必须重写<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类以返回你的版本的新实例化<xref:Microsoft.VisualStudio.Package.ExpansionFunction>你支持每个扩展函数的类。 如果支持扩展函数从可能的值的列表，还必须重写<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A>中的方法<xref:Microsoft.VisualStudio.Package.ExpansionFunction>类以返回这些值的列表。  
  
 采用参数或需要访问其他字段的扩展函数不应为与可编辑字段，如扩展提供程序。 可能未完全初始化由扩展函数调用的时间。 因此，扩展函数不能获取其自变量或任何其他字段的值。  
  
### <a name="example"></a>示例  
 下面是一个示例的简单易用的扩展函数的调用方式`GetName`可能实现。 此扩展函数后面加一个数字基类名称实例化扩展函数每次 （这对应于每个时间相关联的代码段插入）。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [旧语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [代码片段](../../ide/code-snippets.md)   
 [演练：获取安装代码片段（旧版实现）的列表](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)