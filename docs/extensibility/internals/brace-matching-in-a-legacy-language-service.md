---
title: "传统语言服务中的括号匹配 | Microsoft Docs"
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
  - "大括号匹配"
  - "语言服务 [托管的包框架]，大括号匹配"
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# 传统语言服务中的括号匹配
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

大括号匹配可帮助开发人员跟踪需要一起发生，例如括号和大括号的语言元素。 当开发人员输入一个右大括号时，左大括号突出显示。  
  
 您可以匹配两个或三个一起出现的元素，称为对和三元组。 三元组是三个一起出现的元素的集合。 例如，在 C\# 中， `foreach` 语句窗体构成三元组:"`foreach()`"，"`{`"，并"`}`"。 键入右大括号时，将突出显示所有三个元素。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现大括号匹配的新方法的详细信息，请参阅 [演练︰ 显示匹配的大括号](../../extensibility/walkthrough-displaying-matching-braces.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 类支持这两个对，用两倍 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> 和 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> 方法。  
  
## 实现  
 语言服务需要确定在语言中的所有匹配的元素，然后找到所有配对。 这通常通过实现 <xref:Microsoft.VisualStudio.Package.IScanner> 来检测匹配的语言，然后使用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法，以匹配的元素。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法调用扫描仪以标记行并返回之前插入符号的标记。 扫描程序指示已通过设置的令牌触发器值找到的语言元素对 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 上当前的令牌。<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法调用 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 方法又调用 <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> 具有分析原因值的方法 <xref:Microsoft.VisualStudio.Package.ParseReason> 中查找匹配的语言元素。 当找到匹配的语言元素时，这两个元素将突出显示。  
  
 键入一个括号触发的方式的大括号突出显示的完整说明，请参阅主题中的"示例分析操作"节 [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。  
  
## 启用支持大括号匹配  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 属性可以设置 `MatchBraces`, ，`MatchBracesAtCaret`, ，和 `ShowMatchingBrace` 命名设置相应的属性的参数，则 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 类。 此外可以由用户设置语言首选项属性。  
  
|注册表项|属性|描述|  
|----------|--------|--------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|启用大括号匹配|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|启用大括号匹配插入符号移动。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|突出显示匹配的括号。|  
  
## 匹配的条件语句  
 您可以条件与语句相匹配，如 `if`, ，`else if`, ，和 `else`, ，或 `#if`, ，`#elif`, ，`#else`, ，`#endif`, ，方式与匹配的分隔符相同。 您可以子类化 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 类，并提供了可以添加文本的方法跨以及内部数组的匹配元素的分隔符。  
  
## 设置触发器  
 下面的示例演示如何检测匹配的括号、 大括号和括号，以及在扫描仪中为其设置触发器。<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法 <xref:Microsoft.VisualStudio.Package.Source> 类检测到触发器并调用分析器以找到 （请参阅本主题中的"查找匹配"部分） 的匹配对。 此示例是仅供说明用途。 它假定您的扫描仪，包含一种方法 `GetNextToken` ，标识并返回从文本行的令牌。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private const string braces = "()[]{}";  
        private Lexer lex;  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar) && token.Length > 0)  
                {  
                    if (braces.IndexOf(firstChar) != -1)  
                    {  
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;  
                    }  
                }  
            }  
            return foundToken;  
        }  
```  
  
## 匹配括在括号内  
 下面是一个简化的示例相匹配的语言元素 {}，（） 和 \[\]，并在添加到其范围 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 对象。 此方法是不建议使用该方法对分析源代码;它是仅供说明用途。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class Parser  
    {  
         private IList<TextSpan[]> m_braces;  
         public IList<TextSpan[]> Braces  
         {  
             get { return m_braces; }  
         }  
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             if IsMatch(braceSpan1, braceSpan2)  
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });  
         }  
  
         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             //definition for matching here  
          }  
    }  
  
    public class TestLanguageService : LanguageService  
    {  
         Parser parser = new Parser();  
         Source source = (Source) this.GetSource(req.FileName);  
  
         private AuthoringScope ParseSource(ParseRequest req)  
         {  
             if (req.Sink.BraceMatching)  
             {  
                 if (req.Reason==ParseReason.MatchBraces)  
                 {  
                     foreach (TextSpan[] brace in parser.Braces)  
                     {  
                         req.Sink.MatchPair(brace[0], brace[1], 1);  
                     }  
                 }  
             }  
             return new TestAuthoringScope();  
         }  
    }  
}  
```  
  
## 请参阅  
 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [旧的语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)