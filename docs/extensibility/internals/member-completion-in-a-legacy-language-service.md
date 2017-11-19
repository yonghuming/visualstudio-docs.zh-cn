---
title: "在旧语言服务的成员自动补全 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ee8dd14674a1157eefda60e2e7536d7ade90f79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="member-completion-in-a-legacy-language-service"></a>在旧语言服务的成员自动补全
IntelliSense 成员完成为工具提示显示特定的作用域，如类、 结构、 枚举或命名空间的可能成员的列表。 例如，在 C# 中，如果用户键入"this"跟一个句点的类或结构在当前范围内的所有成员的列表显示，用户可以从中选择的列表中。  
  
 托管的包框架 (MPF) 提供的工具提示和管理的列表中的工具提示; 的支持需要的是来自分析器提供显示在列表中的数据的协作。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解详细信息，请参阅[扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="how-it-works"></a>它是如何工作  
 中的成员列表中均显示使用 MPF 类的两种方法如下：  
  
-   在标识符上或成员完成字符之后定位插入符号，并选择**列表成员**从**IntelliSense**菜单。  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner>扫描程序检测到一个成员完成字符和设置的令牌触发器<xref:Microsoft.VisualStudio.Package.TokenTriggers>，该字符。  
  
 一个成员完成字符指示的类、 结构或枚举成员将遵循。 例如，在 C# 或 Visual Basic 成员完成字符是`.`，而 c + + 中的字符是`.`或`->`。 扫描成员选择字符时，设置触发器值。  
  
### <a name="the-intellisense-member-list-command"></a>IntelliSense 成员列表命令  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令启动对的调用<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法<xref:Microsoft.VisualStudio.Package.Source>类和<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法，反过来，调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法分析器分析原因为<xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
 分析器确定当前的位置，以及下或紧接在当前的位置之前的令牌的上下文。 根据此令牌，显示的声明列表。 例如，在 C# 中，如果您定位类成员并选择脱字号**列表成员**，获取类的所有成员的列表。 如果遵循对象变量一段时间后将插入符号，你将获取对象所表示的所有成员的类的列表。 请注意，是否脱字号位于成员在成员列表中显示时，从列表中选择成员替代脱字号位于与列表中的成员。  
  
### <a name="the-token-trigger"></a>令牌的触发器  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>触发器启动对的调用<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法<xref:Microsoft.VisualStudio.Package.Source>类和<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法，反过来，调用分析原因为分析器<xref:Microsoft.VisualStudio.Package.ParseReason>(如果该令牌的触发器还包含<xref:Microsoft.VisualStudio.Package.TokenTriggers>标志，分析原因是<xref:Microsoft.VisualStudio.Package.ParseReason>它可以合并成员选择和大括号突出显示)。  
  
 分析器确定当前的上下文以及之前成员选择字符具有已键入内容位置。 中的信息，分析器将创建的所有成员的请求的作用域的列表。 声明此列表存储在<xref:Microsoft.VisualStudio.Package.AuthoringScope>从返回的对象<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。 如果返回任何声明，将显示成员完成工具提示。 由的实例管理的工具提示<xref:Microsoft.VisualStudio.Package.CompletionSet>类。  
  
## <a name="enabling-support-for-member-completion"></a>启用对成员完成的支持  
 你必须具有`CodeSense`注册表项设置为 1 可支持任何智能感知操作。 此注册表项可以设置使用命名参数传递给<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>语言包与关联的用户属性。 语言服务类读取中此注册表项的值<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>属性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。  
  
 如果你扫描程序返回的令牌触发器<xref:Microsoft.VisualStudio.Package.TokenTriggers>，你的分析程序返回的声明，列表，然后显示成员的完成列表。  
  
## <a name="supporting-member-completion-in-the-scanner"></a>在扫描程序的支持成员自动补全  
 扫描仪必须能够检测成员完成字符和设置的令牌触发器<xref:Microsoft.VisualStudio.Package.TokenTriggers>时分析该字符。  
  
### <a name="example"></a>示例  
 下面是检测成员完成字符并设置适当的简化的示例<xref:Microsoft.VisualStudio.Package.TokenTriggers>标志。 此示例是仅供说明用途。 它假定你扫描程序包含一个方法`GetNextToken`用于标识并返回从文本行的令牌。 示例代码只需设置该触发器，只要它发现正确的字符类型。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>分析器中的支持成员自动补全  
 为成员完成<xref:Microsoft.VisualStudio.Package.Source>类调用<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>方法。 你必须派生自的类中实现列表<xref:Microsoft.VisualStudio.Package.Declarations>类。 请参阅<xref:Microsoft.VisualStudio.Package.Declarations>类必须实现的方法有关的详细信息。  
  
 使用调用分析器<xref:Microsoft.VisualStudio.Package.ParseReason>或<xref:Microsoft.VisualStudio.Package.ParseReason>时键入成员选择字符。 给定的位置<xref:Microsoft.VisualStudio.Package.ParseRequest>对象后立即成员选择字符。 分析器必须收集可以出现在该特定点的源代码中的成员列表中的所有成员的名称。 然后分析器必须分析以确定用户与成员选择字符相关联的作用域的当前行。  
  
 在成员选择字符之前，此范围根据标识符的类型。 例如，在 C# 中，给定成员变量`languageService`具有一种`LanguageService`，键入**languageService。** 生成的所有成员的列表`LanguageService`类。 此外在 C# 中，键入**这。** 产生的当前作用域中的类的所有成员的列表。  
  
### <a name="example"></a>示例  
 下面的示例演示一种方法来填充<xref:Microsoft.VisualStudio.Package.Declarations>列表。 此代码假定分析器构造声明并将其添加到列表，通过调用`AddDeclaration`方法`TestAuthoringScope`类。  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```