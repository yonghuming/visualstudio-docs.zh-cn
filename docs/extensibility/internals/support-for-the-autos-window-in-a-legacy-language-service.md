---
title: "支持传统语言服务中的自动窗口 |Microsoft 文档"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 88cff53ca5c335fdf60aef85d79e9c6e86f03cfa
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>对旧语言服务中的自动窗口的支持
**自动**窗口将显示如变量和参数 （无论由于断点或异常） 暂停正在调试的程序时在作用域中的表达式。 表达式可以包含本地或全局变量和局部范围中进行了更改的参数。 **自动**窗口还可以包括类、 结构或某些其他类型的实例化。 表达式计算器可以计算的任何内容可能会显示在**自动**窗口。  
  
 托管的包框架 (MPF) 不提供直接支持**自动**窗口。 但是，如果重写<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法，可以返回表达式的值以显示在列表**自动**窗口。</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>  
  
## <a name="implementing-support-for-the-autos-window"></a>实现对自动窗口的支持  
 只需执行的操作支持**自动**窗口是实现<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>中方法的<xref:Microsoft.VisualStudio.Package.LanguageService>类。</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 您的实现必须确定，给定表达式应出现在源文件中的某个位置**自动**窗口。 该方法返回字符串，其中每个字符串均表示一个表达式的列表。 返回值为<xref:Microsoft.VisualStudio.VSConstants.S_OK>指示列表包含表达式，而<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>指示没有要显示的表达式。</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
 返回的实际表达式是变量或参数出现在代码中的该位置的名称。 这些名称传递给表达式计算器才能获取值和类型，然后显示在**自动**窗口。  
  
### <a name="example"></a>示例  
 下面的示例演示<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>用于获取从<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法使用的分析原因<xref:Microsoft.VisualStudio.Package.ParseReason>。</xref:Microsoft.VisualStudio.Package.ParseReason></xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>表达式的列表的方法</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>的实现 每个表达式包装为`TestVsEnumBSTR`实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>接口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>  
  
 请注意，`GetAutoExpressionsCount`和`GetAutoExpression`方法上都是自定义方法`TestAuthoringSink`对象，并添加了以支持此示例。 它们代表一种方式添加到哪些表达式`TestAuthoringSink`分析器的对象 (通过调用<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>方法) 可以从分析器外部访问。</xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>  
  
```c#  
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
