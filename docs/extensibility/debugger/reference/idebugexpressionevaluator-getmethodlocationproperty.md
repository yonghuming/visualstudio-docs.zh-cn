---
title: "IDebugExpressionEvaluator::GetMethodLocationProperty |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 11
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
ms.openlocfilehash: 592a3401d0f9712a78fcab9cf1056b05c6a746b8
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
此方法将具有方法位置和偏移量转换为内存地址。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>参数  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in]方法位置和偏移量，表示为字符串。  
  
 `pSymbolProvider`  
 [in]符号提供程序表示为[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)对象。  
  
 `pAddress`  
 [in]在方法中，表示为一个地址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)对象。  
  
 `pBinder`  
 [in]联编程序表示为[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)对象。  
  
 `ppProperty`  
 [out]返回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示的内存地址的接口。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 可以使用返回的地址，例如设置断点。  
  
 不管名称如何`upstrFullyQualifiedMethodPlusOffset`，此参数可以传递部分限定的方法名称。 在这种情况下，所选的方法是包含一个`pAddress`。 如何解释此参数是由表达式计算器以及它支持的语言的实现。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
