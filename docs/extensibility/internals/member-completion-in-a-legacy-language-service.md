---
title: "在早期语言服务中的成员完成 | Microsoft Docs"
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
  - "IntelliSense、 成员完成工具提示"
  - "成员完成时，支持的语言服务 [托管的包框架]"
  - "语言服务 [托管的包框架] IntelliSense 成员完成"
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 在早期语言服务中的成员完成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense 成员完成法是工具提示显示特定的作用域，例如类、 结构、 枚举或命名空间的可能的成员的列表。 例如，在 C\# 中，状态下，如果用户键入"this"后, 跟一个句点，类或结构当前范围内的所有成员的列表将出现在列表中，用户可以从中选择。  
  
 托管的包框架 \(MPF\) 提供支持用于工具提示和管理的列表中的工具提示。所需要的是来自分析器提供显示在列表中的数据的合作。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要获得详细信息，请参阅 [扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 它是如何工作  
 中的成员列表中均显示使用 MPF 类的两种方式如下︰  
  
-   一个标识符，或者在成员完成字符后定位脱字号和选择 **列表成员** 从 **IntelliSense** 菜单。  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner> 扫描仪检测成员完成字符和设置的令牌触发器 <xref:Microsoft.VisualStudio.Package.TokenTriggers> ，该字符。  
  
 成员完成字符指示的类、 结构或枚举成员将遵循。 例如，在 C\# 或 Visual Basic 成员完成字符是 `.`, ，而在 c \+ \+ 字符是 `.` 或 `->`。 当扫描成员选择字符集时设置触发器值。  
  
### 智能感知成员列表命令  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令启动对调用 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法 <xref:Microsoft.VisualStudio.Package.Source> 类和 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，反过来，调用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法分析器中分析的原因的 <xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
 分析器确定当前的位置，以及下或当前的位置之前立即的令牌的上下文。 根据此标记，显示声明的列表。 例如，在 C\# 中，如果定位在某个类成员并选择插入符号 **列表成员**, ，获取类的所有成员的列表。 如果遵循对象变量一段时间后定位脱字号，请将类的对象所表示的所有成员的列表。 请注意，是否成员列表中显示时，插入符号定位在成员上，从列表中选择成员替代脱字号所在的一个列表中的成员。  
  
### 令牌的触发器  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 触发器启动调用 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法 <xref:Microsoft.VisualStudio.Package.Source> 类和 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，反过来，调用分析原因为分析器 <xref:Microsoft.VisualStudio.Package.ParseReason> \(如果该令牌的触发器还包括 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 标志，分析原因是 <xref:Microsoft.VisualStudio.Package.ParseReason> 此功能结合了成员选择和大括号突出显示\)。  
  
 分析器确定当前的上下文位置及键入的内容之前该成员选择字符。 中的信息，分析器将创建请求的作用域中的所有成员的列表。 此声明的列表存储在 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 从返回的对象 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。 如果返回的任何声明，将显示成员完成工具提示。 实例管理的工具提示 <xref:Microsoft.VisualStudio.Package.CompletionSet> 类。  
  
## 启用对成员完成的支持  
 您必须具有 `CodeSense` 注册表项设置为 1 可支持任何智能感知操作。 此注册表项可以设置使用命名参数传递给 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 与语言包相关联的用户属性。 语言服务类读取来自此注册表项的值 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 属性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。  
  
 如果您的扫描仪返回的令牌触发器 <xref:Microsoft.VisualStudio.Package.TokenTriggers>, ，而且您的分析程序返回列表的声明，则显示成员完成列表。  
  
## 在扫描程序中支持成员完成  
 扫描仪必须能够检测成员完成字符并设置的令牌触发器 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 时分析该字符。  
  
### 示例  
 下面是一个简化的示例检测成员完成字符并设置适当 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 标志。 此示例是仅供说明用途。 它假定您的扫描仪，包含一种方法 `GetNextToken` ，标识并返回从文本行的令牌。 示例代码只需设置该触发器，只要它发现正确类型的字符。  
  
```c#  
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
  
## 在分析器中支持成员完成  
 为成员完成 <xref:Microsoft.VisualStudio.Package.Source> 类将调用 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 方法。 您必须在派生自的类中实现列表 <xref:Microsoft.VisualStudio.Package.Declarations> 类。 请参阅 <xref:Microsoft.VisualStudio.Package.Declarations> 类必须实现的方法有关的详细信息。  
  
 使用调用分析器 <xref:Microsoft.VisualStudio.Package.ParseReason> 或 <xref:Microsoft.VisualStudio.Package.ParseReason> 时键入成员选择字符。 指定的位置 <xref:Microsoft.VisualStudio.Package.ParseRequest> 对象后立即成员选择字符。 分析器必须收集可以出现在源代码中该特定时刻的成员列表中的所有成员的名称。 然后分析器必须分析当前的行，以确定用户与成员选择字符相关联的作用域。  
  
 成员选择字符之前，此作用域取决于标识符的类型。 例如，在 C\# 中，给定成员变量 `languageService` 具有一种类型的 `LanguageService`, 、 键入 **languageService。** 生成的所有成员的列表 `LanguageService` 类。 此外在 C\# 中，键入 **这。** 生成当前作用域中的类的所有成员的列表。  
  
### 示例  
 下面的示例演示一种方法来填充 <xref:Microsoft.VisualStudio.Package.Declarations> 列表。 此代码假定分析器构造一个声明，并将其添加到列表中，通过调用 `AddDeclaration` 方法 `TestAuthoringScope` 类。  
  
```c#  
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