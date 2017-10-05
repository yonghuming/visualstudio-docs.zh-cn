---
title: "实现表达式的计算示例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
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
ms.openlocfilehash: ca872421d20d1d1a85cb2c5db621de28adee356d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="sample-implementation-of-expression-evaluation"></a>表达式计算的实现示例
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 有关**监视**窗口表达式中，Visual Studio 调用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)生成[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)对象。 `IDebugExpressionContext2::ParseText`实例化的表达式计算器 (EE) 和调用[分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)获取[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)对象。  
  
 此实现的`IDebugExpressionEvaluator::Parse`将执行以下任务：  
  
1.  [C + +]分析表达式来查找错误。  
  
2.  实例化类 (调用`CParsedExpression`在此示例中) 实现`IDebugParsedExpression`接口，并将存储在类中要分析的表达式。  
  
3.  返回`IDebugParsedExpression`接口从`CParsedExpression`对象。  
  
> [!NOTE]
>  在下面的示例中以及 MyCEE 示例中，表达式计算器不分隔从评估分析。  
  
## <a name="managed-code"></a>托管代码  
 这是实现`IDebugExpressionEvaluator::Parse`在托管代码中。 请注意此版本的方法将推迟到分析[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)如分析的代码还可以计算在同一时间 (请参阅[监视表达式求值](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>非托管代码  
 这是实现`IDebugExpressionEvaluator::Parse`非托管代码中。 此方法调用 helper 函数， `Parse`，以便分析表达式并检查错误，但此方法将忽略所得到的值。 正式评估推迟到[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)时计算分析表达式 (请参阅[监视表达式求值](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
```cpp  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [监视窗口表达式求值](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [计算监视表达式](../../extensibility/debugger/evaluating-a-watch-expression.md)
