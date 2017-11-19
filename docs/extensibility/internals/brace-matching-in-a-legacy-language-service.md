---
title: "旧语言服务中的括号匹配 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd70d65a7d2cbabbbf7fcd3581e8ba974ff25ee2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="brace-matching-in-a-legacy-language-service"></a>旧语言服务中的括号匹配
大括号匹配可帮助开发人员跟踪发生在一起，例如圆括号和大括号所需要的语言元素。 当开发人员进入右大括号时，突出显示左大括号。  
  
 你可以匹配两个或三个共同匹配的元素，称为对和三元组。 三元组是三个共同匹配元素的集合。 例如，在 C# 中，`foreach`语句窗体三元组:"`foreach()`"，"`{`"，和"`}`"。 如果类型的右大括号，则将突出显示所有三个元素。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现大括号匹配的新方式的详细信息，请参阅[演练： 显示匹配的大括号](../../extensibility/walkthrough-displaying-matching-braces.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>类支持这两个对的数据集与<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A>和<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>方法。  
  
## <a name="implementation"></a>实现  
 语言服务需要识别所有匹配的元素的语言，然后查找匹配的所有对。 这通常通过实现实现<xref:Microsoft.VisualStudio.Package.IScanner>检测匹配的语言，然后使用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法可以进行匹配的元素。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法调用的扫描程序，以标记行并返回之前插入符号的令牌。 扫描程序表示已通过设置的一个令牌触发器值找到了一个语言元素对<xref:Microsoft.VisualStudio.Package.TokenTriggers>上当前的令牌。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法调用<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>反过来调用的方法<xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A>带有分析原因值的方法<xref:Microsoft.VisualStudio.Package.ParseReason>查找匹配的语言元素。 当找到匹配的语言元素时，将突出显示这两个元素。  
  
 有关如何键入大括号触发的大括号突出显示的完整说明，请参阅主题中的"示例分析操作"部分[旧语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。  
  
## <a name="enabling-support-for-brace-matching"></a>为大括号匹配启用支持  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性可以设置`MatchBraces`， `MatchBracesAtCaret`，和`ShowMatchingBrace`命名设置的相应属性的参数<xref:Microsoft.VisualStudio.Package.LanguagePreferences>类。 语言首选项属性也可以由用户设置。  
  
|注册表项|属性|描述|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|启用大括号匹配|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|启用大括号匹配作为脱字号移动。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|突出显示匹配的括号。|  
  
## <a name="matching-conditional-statements"></a>匹配的条件语句  
 你可以如匹配条件语句`if`， `else if`，和`else`，或`#if`， `#elif`， `#else`， `#endif`，方式与匹配的分隔符相同。 你可以子类化<xref:Microsoft.VisualStudio.Package.AuthoringSink>类并提供可以添加文本的方法跨以及分隔符对的匹配元素内部的数组。  
  
## <a name="setting-the-trigger"></a>设置触发器  
 下面的示例演示如何检测匹配的括号、 大括号和括号，和在扫描程序中为其设置触发器。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法<xref:Microsoft.VisualStudio.Package.Source>类检测到触发器和调用分析器查找匹配的对 （请参阅本主题中的"查找匹配项"一节）。 此示例是仅供说明用途。 它假定你扫描程序包含一个方法`GetNextToken`用于标识并返回从文本行的令牌。  
  
```csharp  
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
  
## <a name="matching-the-braces"></a>匹配的大括号  
 下面是有关匹配的语言元素 {}、 （），和 []，以及添加到其范围的简化的示例<xref:Microsoft.VisualStudio.Package.AuthoringSink>对象。 此方法不是对分析源代码; 建议的方法它是仅供说明用途。  
  
```csharp  
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
  
## <a name="see-also"></a>另请参阅  
 [旧语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [旧版语言服务分析器和扫描程序](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)