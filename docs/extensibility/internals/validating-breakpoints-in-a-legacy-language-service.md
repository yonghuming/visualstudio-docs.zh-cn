---
title: "验证旧语言服务中的断点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3a8c2df45c0a834430a499cf6a7e7ef2da10bdbf
ms.lasthandoff: 02/22/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>验证旧语言服务中的断点
断点指示程序执行应在某一特定点处停止，在调试器中运行时。 用户可以在源文件中的任意行上放置一个断点，因为编辑器并不了解何谓断点的有效位置。 当启动调试器时，所有 （称为挂起断点） 的标记断点将绑定到正在运行的程序中的相应位置。 在同一时间断点进行验证，以便确保它们标记的有效代码位置。 例如上一条注释, 的断点无效，因为在该位置在源代码中没有任何代码。 调试器将禁用无效的断点。  
  
 语言服务就会了解有关所显示的源代码，因为它可以验证断点，之后再启动调试器。 您可以重写<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法以返回指定一个有效位置，断点的范围。</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 当启动调试器，但无需等待要加载的调试器的无效断点会通知用户时，断点位置仍进行验证。  
  
## <a name="implementing-support-for-validating-breakpoints"></a>实现支持用于验证断点  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法为给定的断点的位置。</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 位置是否不是有效的并指示这通过返回一个标识的代码的文本范围与相关联的行位置断点，必须确定您的实现。  
  
-   返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>位置是否有效，或<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>如果该令牌无效。</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
-   如果断点有效的文本范围将突出显示以及断点。  
  
-   如果断点无效，状态栏中显示一条错误消息。  
  
### <a name="example"></a>示例  
 此示例演示如何实现<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>指定位置处调用分析器以获取代码的范围 （如果有） 的方法。</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>  
  
 此示例假定你已添加了`GetCodeSpan`方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>类，用于验证的文本范围和返回`true`如果它是有效的断点位置。</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
```c#  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [遗留语言服务功能](../../extensibility/internals/legacy-language-service-features1.md)
