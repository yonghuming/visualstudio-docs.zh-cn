---
title: "IDebugExpressionEvaluator | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator 接口"
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示表达式计算器。  
  
## 语法  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## 实施者注意事项  
 表达式计算器必须实现此接口。  
  
## 调用方的说明  
 若要获得此接口，实例化表达式计算器通过 `CoCreateInstance` 方法通过使用该计算器的类 ID \(CLSID\)。 请参阅示例。  
  
## Vtable 顺序中的方法  
 下表显示的方法 `IDebugExpressionEvaluator`。  
  
|方法|描述|  
|--------|--------|  
|[分析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|将一个表达式字符串转换为分析的表达式。|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|获取本地变量、 参数和方法的其他属性。|  
|[GetMethodLocationProperty](../Topic/IDebugExpressionEvaluator::GetMethodLocationProperty.md)|将具有方法位置和偏移量转换为内存地址。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|确定要用于创建可打印结果的语言。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|设置的注册表根目录。 用于通过并行调试。|  
  
## 备注  
 在典型的情况下，调试引擎 \(DE\) 进行实例化表达式计算器 \(EE\) 作为的调用结果 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 DE 由于 DE 知道的语言和 EE 它想要使用的供应商联系，从注册表获取 EE 的 CLSID \( [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 函数， `GetEEMetric`, ，可以帮助完成此检索\)。  
  
 DE EE 实例化后，调用 [分析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 分析表达式并将其存储在 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 对象。 更高版本，对的调用 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 计算表达式的值。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 示例  
 此示例演示如何实例化表达式计算器中的源代码中给出符号提供程序和地址。 此示例使用一个函数， `GetEEMetric`, ，从 [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 库、 dbgmetric.lib。  
  
```cpp#  
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,  
                                                 IDebugAddress *pSourceAddress)  
{  
    // This is typically defined globally but is specified here just  
    // for this example.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
  
    IDebugExpressionEvaluator *pEE = NULL;  
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {  
        HRESULT hr         = S_OK;  
        GUID  languageGuid = { 0 };  
        GUID  vendorGuid   = { 0 };  
  
        hr = pSymbolProvider->GetLanguage(pSourceAddress,  
                                          &languageGuid,  
                                          &vendorGuid);  
        if (SUCCEEDED(hr)) {  
            CLSID clsidEE      = { 0 };  
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;  
            // Get the expression evaluator's CLSID from the registry.  
            ::GetEEMetric(languageGuid,  
                          vendorGuid,  
                          metricCLSID,  
                          &clsidEE,  
                          strRegistrationRoot);  
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {  
                // Instantiate the expression evaluator.  
                spExpressionEvaluator.CoCreateInstance(clsidEE);  
            }  
            if (spExpressionEvaluator != NULL) {  
                pEE = spExpressionEvaluator.Detach();  
            }  
        }  
    }  
    return pEE;  
}  
```  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)