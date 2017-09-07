---
title: "支持旧语言服务中的自动窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 12
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b6e4f4783bd4d968ad7ab4784cdd6bb32ba2392a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>支持旧语言服务中的自动窗口
**自动**窗口显示如变量和参数，位于范围内时被调试的程序已暂停 （或者由于断点或异常） 的表达式。 表达式可以包含变量，本地或全局和局部范围中进行了更改的参数。 **自动**窗口还可以包括类、 结构或某些其他类型的实例化。 表达式计算器可以计算的任何内容可能显示在**自动**窗口。  
  
 托管的包框架 (MPF) 不提供直接支持**自动**窗口。 但是，如果你重写<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法，你可以返回表达式的值以显示列表**自动**窗口。  
  
## <a name="implementing-support-for-the-autos-window"></a>实现对自动窗口的支持  
 你只需要做，以支持**自动**窗口是实现<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。 您的实现必须确定，给定表达式应出现在源文件中的位置**自动**窗口。 该方法返回字符串，其中每个字符串都表示一个表达式的列表。 返回值<xref:Microsoft.VisualStudio.VSConstants.S_OK>指示列表是否包含表达式，而<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>指示没有要显示的表达式。  
  
 返回的实际表达式是变量或出现在代码中的该位置的参数的名称。 这些名称传递给表达式计算器才能获取值和类型会随后显示在**自动**窗口。  
  
### <a name="example"></a>示例  
 下面的示例演示如何实现<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>获取从表达式列表的方法<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法使用的分析原因<xref:Microsoft.VisualStudio.Package.ParseReason>。 每个表达式包装为`TestVsEnumBSTR`实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>接口。  
  
 请注意，`GetAutoExpressionsCount`和`GetAutoExpression`方法上都是自定义方法`TestAuthoringSink`对象，并添加了以支持此示例。 它们表示一种方式添加到哪个表达式`TestAuthoringSink`分析器的对象 (通过调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>方法) 可以分析器外部访问。  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
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
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
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
