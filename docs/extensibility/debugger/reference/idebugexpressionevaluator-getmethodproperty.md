---
title: "IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty 方法"
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取包含局部变量、参数和方法的其他属性的属性对象。  
  
## 语法  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### 参数  
 `pSymbolProvider`  
 \[in\] 要使用的符号提供程序，表示为 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 对象。  
  
 `pAddress`  
 \[in\] 在代码中的地址，是以 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象，应该解析到最近的包含功能。  
  
 `pBinder`  
 \[in\] 要使用的联编程序，表示为 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 对象。  
  
 `fIncludeHiddenLocals`  
 \[in\] 非零 \(`TRUE`\) 表示包括隐藏的本地;零 \(0\)`FALSE`\) 的含义保留掩藏起来的本地  
  
 `ppProperty`  
 \[out\] 返回表示方法的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 隐藏的本地通常是由编译器生成的变量。  
  
## 请参阅  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)