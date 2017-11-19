---
title: "参数信息，请参阅旧语言 Service2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d806c48cd96c93774b77363f1d427968613e60b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>参数信息，请参阅旧语言服务
IntelliSense 参数信息是在用户键入的参数列表时显示方法的签名的工具提示启动的方法参数列表的字符 （通常左括号）。 在输入每个参数和类型的参数分隔符 （通常为逗号） 时，工具提示将更新以显示下一个参数以粗体显示。  
  
 托管的包框架 (MPF) 类提供用于管理参数信息工具提示的支持。 分析器必须检测参数启动，则参数接下来，并且参数结束字符，并且它必须提供的方法签名和其关联的参数的列表。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解详细信息，请参阅[扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="implementation"></a>实现  
 分析器应将触发器值设置<xref:Microsoft.VisualStudio.Package.TokenTriggers>找到参数列表起始字符 （通常左括号） 时设置。 它应设置<xref:Microsoft.VisualStudio.Package.TokenTriggers>找到参数分隔符 （通常以逗号） 时触发。 这将导致得以更新并重显示下一个参数以粗体显示的参数信息工具提示。 分析器应将触发器值设置<xref:Microsoft.VisualStudio.Package.TokenTriggers>时如果找到参数列表结束字符 （通常右括号）。  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>触发器值开始调用<xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A>方法，后者反过来调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法分析器分析原因为<xref:Microsoft.VisualStudio.Package.ParseReason>。 如果分析器确定参数列表的开始字符之前的标识符是可识别的方法名称时，它返回的匹配中的方法签名的列表<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象。 如果找到任何方法签名，则会显示在列表中的第一个签名的参数信息工具提示。 按照多个签名键入，然后将更新此工具提示。 如果类型参数列表结束字符，将从视图中删除参数信息工具提示。  
  
> [!NOTE]
>  若要确保参数信息工具提示的格式是否正确，必须在重写的属性<xref:Microsoft.VisualStudio.Package.Methods>类提供的相应字符。 基<xref:Microsoft.VisualStudio.Package.Methods>类假定 C# 的样式方法签名。 请参阅<xref:Microsoft.VisualStudio.Package.Methods>有关如何执行此操作的详细信息的类。  
  
## <a name="enabling-support-for-the-parameter-info"></a>启用对参数信息的支持  
 若要支持参数信息工具提示，必须设置`ShowCompletion`命名的参数<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>到`true`。 语言服务读取中此注册表项的值<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>属性。  
  
 此外，<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>属性必须设置为`true`的参数信息工具提示显示。  
  
### <a name="example"></a>示例  
 下面是检测的参数列表字符并设置相应的触发器的简化的示例。 此示例是仅供说明用途。 它假定你扫描程序包含一个方法`GetNextToken`用于标识并返回从文本行的令牌。 示例代码只需设置触发器，只要它发现正确的字符类型。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>在分析器中支持的参数信息工具提示  
 <xref:Microsoft.VisualStudio.Package.Source>类进行某些假设的内容<xref:Microsoft.VisualStudio.Package.AuthoringScope>和<xref:Microsoft.VisualStudio.Package.AuthoringSink>类显示和更新参数信息工具提示时。  
  
-   给定分析器<xref:Microsoft.VisualStudio.Package.ParseReason>时键入参数列表的起始字符。  
  
-   给定的位置<xref:Microsoft.VisualStudio.Package.ParseRequest>对象是参数列表的开始字符后立即。 分析器必须收集的签名的所有可用在方法声明的位置并将其存储在你的版本的列表中<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象。 此列表包括方法名称、 方法类型 （或返回类型），以及可能的参数的列表。 更高版本的方法签名或签名的参数信息工具提示中显示搜索此列表。  
  
 分析器必须然后分析由指定的行<xref:Microsoft.VisualStudio.Package.ParseRequest>键入参数处于对象来收集输入的方法以及多久完成用户的名称。 这通过将传递到方法的名称来实现<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>对象，然后再调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>分析方法的参数列表的开始字符时，调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>方法时的参数列表下一个字符会分析，并最后调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>方法分析参数列表结束字符时。 通过使用这些方法调用的结果<xref:Microsoft.VisualStudio.Package.Source>类相应地更新参数信息工具提示。  
  
### <a name="example"></a>示例  
 下面是文本的用户可输入行。 行下方，数字指示哪个步骤均由分析器 （假设分析移动从左到右） 的行中的该位置。 此处的假设条件是，在行之前的所有内容已分析的方法签名，包括"testfunc"方法签名。  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 分析器采用的步骤如下所述：  
  
1.  分析器调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>带有文本"testfunc"。  
  
2.  分析器调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>。  
  
3.  分析器调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>。  
  
4.  分析器调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>。