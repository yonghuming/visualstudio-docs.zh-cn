---
title: "对旧语言服务中的代码段的支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "支持的语言服务的代码段"
  - "代码段，支持的语言服务 [托管的包框架]"
  - "支持代码段的语言服务 [托管的包框架]"
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# 对旧语言服务中的代码段的支持
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

代码段是一段代码将插入到源文件。 在代码段是一组字段的基于 XML 的模板。 插入代码段，并可以具有不同的值，具体取决于在该表中插入代码段的上下文后，将突出显示这些字段。 立即插入代码段后，该语言服务即可格式化代码段。  
  
 允许代码段以通过使用 TAB 键导航的字段的特殊的编辑模式下插入代码段。 字段可以支持 IntelliSense 样式下拉列表菜单。 用户通过键入 ENTER 或 ESC 键提交到源文件的代码段。 若要了解有关代码段的详细信息，请参阅 [代码段](../../ide/code-snippets.md)。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要获得详细信息，请参阅 [演练: 实现代码段](../../extensibility/walkthrough-implementing-code-snippets.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 管理包的代码段的框架支持  
 托管的包框架 \(MPF\) 支持大多数代码段功能，从正在读取到中插入代码段模板和启用这两个特殊编辑模式。 通过管理支持 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 类。  
  
 当 <xref:Microsoft.VisualStudio.Package.Source> 实例化类时， <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 类调用以获得 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 对象 \(请注意，基 <xref:Microsoft.VisualStudio.Package.LanguageService> 类始终返回一个新 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 为每个对象 <xref:Microsoft.VisualStudio.Package.Source> 对象\)。  
  
 MPF 不支持扩展函数。 扩展函数是一个命名的函数嵌入到代码段模板中并返回一个或多个要放置在一个字段的值。 值将返回由语言服务本身通过 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 对象。<xref:Microsoft.VisualStudio.Package.ExpansionFunction> 对象必须由语言服务以支持扩展函数实现。  
  
## 提供的代码段的支持  
 若要启用的代码段支持，必须提供或安装代码片段，必须提供了一种方法供用户插入这些代码段。 有三个步骤使系统可以支持的代码段 ︰  
  
1.  安装代码段文件。  
  
2.  启用语言服务的代码段。  
  
3.  调用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 对象。  
  
### 安装代码段文件  
 为一种语言的所有代码段存储为 XML 文件中的模板通常代码段模板每个文件。 用于代码段模板的 XML 架构的详细信息，请参阅 [代码段架构参考](../../ide/code-snippets-schema-reference.md)。 每个代码段模板标识与语言 id。 这种语言 ID 在注册表中指定并放入 `Language` 模板中的 \< 代码 \> 标记特性。  
  
 通常有两个代码段模板文件的存储位置的位置 ︰ 1） 的位置安装您的语言以及 2） 在用户的文件夹。 这些位置添加到注册表因此，Visual Studio **代码片段管理器** 可以找到这些代码段。 用户的文件夹是由用户创建的代码段的存储位置。  
  
 已安装的代码段模板文件的典型的文件夹布局外观如下所示 ︰ *\[InstallRoot\]*\\*\[TestLanguage\]*\\Snippets\\*\[LCID\]*\\Snippets。  
  
 *\[InstallRoot\]* 是您的语言安装中的文件夹。  
  
 *\[TestLanguage\]* 是您作为文件夹名称的语言的名称。  
  
 *\[LCID\]* 是区域设置 id。 这是您的代码段的方式本地化的版本存储。 例如，英语的区域设置 ID 为 1033，因此 *\[LCID\]* 都替换为 1033年。  
  
 必须提供一个附加的文件，这是一个索引文件，通常称为 SnippetsIndex.xml 或 ExpansionsIndex.xml （您可以使用任何有效的文件名以.xml 结尾）。 此文件通常存储在 *\[InstallRoot\]*\\*\[TestLanguage\]* 文件夹，指定 snippets 文件夹，以及语言 ID 的确切位置，并使用这些代码段的语言服务的 GUID。 索引文件的准确路径放置在注册表中更高版本中"安装注册表项"所述。 下面是 SnippetsIndex.xml 文件的一个示例 ︰  
  
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
  
 \< 语言 \> 标记指定的语言 ID \( `Lang` 属性\) 和语言服务的 GUID。  
  
 此示例假定已经在 Visual Studio 安装文件夹中安装语言服务。 %LCID%将被替换为用户的当前区域设置 id。 多个 \< SnippetDir \> 标记可以添加，一个用于每个不同的目录和区域设置。 此外，代码段文件夹可以包含子文件夹，其中每个索引文件中用标识 \< SnippetDir \> 标记中嵌入的 \< SnippetSubDir \> 标记。  
  
 用户还可以创建自己的代码段用于您的语言。 这些通常存储在用户的设置文件夹中，例如 *\[TestDocs\]*\\Code Snippets\\*\[TestLanguage\]*\\Test 代码段，其中 *\[TestDocs\]* 是 Visual Studio 的用户的设置文件夹的位置。  
  
 下面的替换元素可将索引文件中的 \< DirPath \> 标记中存储的路径。  
  
|元素|描述|  
|--------|--------|  
|%LCID%|区域设置 id。|  
|%Installroot%|Visual Studio 中，例如，C:\\Program Files\\Microsoft Visual Studio 8 中的根安装文件夹。|  
|%Projdir%|包含当前项目的文件夹。|  
|%Projitem%|包含当前的项目项的文件夹。|  
|%Testdocs%|文件夹中的用户的设置文件夹，例如，C:\\Documents and Settings\\*\[username\]*documents\\visual Studio\\8。|  
  
### 语言服务上启用了代码段  
 您可以为您的语言服务启用代码段，加上 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 属性设为你的 VSPackage \(请参阅 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md) 有关的详细信息\)。<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> 和 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> 参数是可选的但是应该包括 `SearchPaths` 命名参数，以便通知 **代码片段管理器** 您的代码段的位置。  
  
 下面是如何使用此特性的示例 ︰  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### 调用扩展提供程序  
 语言服务控制插入的任何代码段，以及插入调用的方法。  
  
## 调用代码段的扩展提供程序  
 有两种方法可以调用扩展提供程序 ︰ 通过菜单命令或通过从完成列表的快捷方式。  
  
### 通过使用菜单命令插入代码段  
 若要使用菜单命令显示代码段浏览器，添加一个菜单命令，然后调用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 对该菜单命令的响应的接口。  
  
1.  向.vsct 文件中添加命令和一个按钮。 您可以找到说明如何在取消阻止 [演练：使用 Visual Studio 包模板创建菜单命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  从派生类 <xref:Microsoft.VisualStudio.Package.ViewFilter> 类并重写 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> 方法，以指示新的菜单命令的支持。 此示例将始终启用菜单命令。  
  
    ```c#  
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
  
3.  重写 <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.ViewFilter> 类来获取 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 对象，并调用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 对该对象的方法。  
  
    ```c#  
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
  
     中的以下方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 类是由 Visual Studio 按给定顺序过程中调用时插入代码段 ︰  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     之后 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> 方法调用时，在插入代码段和 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 对象是在特殊的编辑模式下用于修改刚插入的代码段。  
  
### 通过使用一种快捷方式插入代码段  
 实现从完成列表的快捷方式是而不是实现菜单命令的复杂得多。 您首先必须将代码段快捷方式添加到智能感知单词完成列表。 然后，您必须检测由于完成而插入代码段快捷方式名称后。 最后，您必须获得的代码段标题和路径中使用的快捷方式名称并传递该信息提供给 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 方法。  
  
 若要将代码段快捷方式添加到完成单词列表中，将它们添加到 <xref:Microsoft.VisualStudio.Package.Declarations> 对象在您 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 类。 必须确保能够识别为代码段名称的快捷方式。 有关示例，请参见 [演练︰ 获取安装的代码段 （旧实现） 的列表](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
 您可以检测到中的代码段快捷方式插入 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> 方法 <xref:Microsoft.VisualStudio.Package.Declarations> 类。 原因是，已将代码段名称插入到源文件中，必须插入扩展时删除它。<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法采用一个描述代码段插入点的范围; 如果在源文件中，范围包括整个代码段名称，该名称替换为代码段。  
  
 以下是版本 <xref:Microsoft.VisualStudio.Package.Declarations> 处理给定快捷名称插入代码段的类。 中的其他方法 <xref:Microsoft.VisualStudio.Package.Declarations> 为了清楚起见省略了类。 请注意，此类的构造函数采用 <xref:Microsoft.VisualStudio.Package.LanguageService> 对象。 这可以从自己版本的传入 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 对象 \(例如，如果您实施的 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 类可能需要 <xref:Microsoft.VisualStudio.Package.LanguageService> 对象在其构造函数并将传递到该对象您 `TestDeclarations` 类构造函数\)。  
  
```  
[C#]  
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
  
 当语言服务获取的快捷名称时，它将调用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> 方法来获取文件名和代码段标题。 语言服务然后调用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 类插入代码段。 在给定的顺序调用下列方法通过 Visual Studio <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 在过程中插入代码段的类 ︰  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 获取语言服务安装的代码段的列表的详细信息，请参阅 [演练︰ 获取安装的代码段 （旧实现） 的列表](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
## 实现 ExpansionFunction 类  
 扩展函数是一个命名的函数嵌入到代码段模板中并返回一个或多个要放置在一个字段的值。 若要在您的语言服务支持扩展函数，您必须从派生类 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 类，实现 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> 方法。 然后，您必须重写 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 类以返回您的版本的新实例化 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 您支持的每个扩展功能的类。 如果支持扩展函数中的可能值的列表，还必须重写 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 类以返回这些值的列表。  
  
 为扩展提供程序可能未完全初始化扩展函数调用时，不采用参数，或需要访问其他字段的扩展函数不应与某个可编辑字段相关联。 因此，扩展函数不能获取它的参数或任何其他字段的值。  
  
### 示例  
 下面是一个示例的简单易用的扩展函数的调用方式 `GetName` 可能实现。 此扩展函数追加一个数字基类名称实例化扩展函数每次 （它对应于每个时间相关联的代码段插入）。  
  
```c#  
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
  
## 请参阅  
 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [注册语言服务](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [代码段](../../ide/code-snippets.md)   
 [演练︰ 获取安装的代码段 （旧实现） 的列表](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)