---
title: "IDebugExpressionEvaluator::GetMethodProperty |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords: IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b80507a0ac3406474f26c6e206ac4d69c43ce27c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
此方法获取一个包含局部变量、 自变量和方法的其他属性的属性对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pSymbolProvider`  
 [in]要使用符号提供程序表示为[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)对象。  
  
 `pAddress`  
 [in]在代码中，表示为地址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)对象，应将解析为最接近的包含函数。  
  
 `pBinder`  
 [in]联编程序要使用，表示为[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)对象。  
  
 `fIncludeHiddenLocals`  
 [in]非零 (`TRUE`) 意味着若要包括隐藏的局部变量; 零 (`FALSE`) 遗漏隐藏局部变量的方法  
  
 `ppProperty`  
 [out]返回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示的方法的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 隐藏的局部变量通常是由编译器生成的变量。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)