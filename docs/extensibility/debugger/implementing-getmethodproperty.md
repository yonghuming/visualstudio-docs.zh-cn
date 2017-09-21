---
title: "实现 GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMethodProperty 方法"
  - "IDebugExpressionEvaluator2 属性"
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 实现 GetMethodProperty
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 Visual Studio 会调用调试引擎 \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), ，从而又会调用 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 来获取有关当前方法的堆栈帧上的信息。  
  
 这种实现 `IDebugExpressionEvaluator::GetMethodProperty` 执行下列任务︰  
  
1.  调用 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), ，并传入 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 对象。 符号提供程序 \(SP\) 将返回 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 表示包含指定的地址的方法。  
  
2.  获取 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 从 `IDebugContainerField`。  
  
3.  实例化一个类 \(称为 `CFieldProperty` 在此示例中\) 实现 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 接口并包含 `IDebugMethodField` SP 从返回的对象  
  
4.  返回 `IDebugProperty2` 接口从 `CFieldProperty` 对象。  
  
## 托管代码  
 此示例演示如何实现 `IDebugExpressionEvaluator::GetMethodProperty` 在托管代码中。  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## 非托管的代码  
 此示例演示如何实现 `IDebugExpressionEvaluator::GetMethodProperty` 非托管代码中。  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## 请参阅  
 [局部变量的实现示例](../../extensibility/debugger/sample-implementation-of-locals.md)