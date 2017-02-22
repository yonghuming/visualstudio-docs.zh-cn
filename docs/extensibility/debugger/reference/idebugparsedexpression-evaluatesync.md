---
title: "IDebugParsedExpression::EvaluateSync | Microsoft Docs"
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
  - "IDebugParsedExpression::EvaluateSync"
helpviewer_keywords: 
  - "IDebugParsedExpression::EvaluateSync 方法"
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法计算已分析的表达式并选择性地将结果为其他数据类型。  
  
## 语法  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### 参数  
 `dwEvalFlags`  
 \[in\] 的 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 常数的组合控件表达式如何将计算。  
  
 `dwTimeout`  
 \[in\] 以毫秒为单位指定最长时间，因此，在返回等待来自此方法。  使用 `INFINITE` 会无限期地等待。  
  
 `pSymbolProvider`  
 \[in\] 符号提供程序，是以 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 接口。  
  
 `pAddress`  
 \[in\] 在方法中执行当前位置，是以 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 接口。  
  
 `pBinder`  
 \[in\] 联编程序，是以 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 接口。  
  
 `bstrResultType`  
 \[in\] 应将该类型结果。  此参数可以为 null 值。  
  
 `ppResult`  
 \[out\] 返回表示计算结果的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 `pAddress`生成一个表达式计算上下文，从而确定所包含的方法来使用语言范围规则确定符号值在表达式中。  
  
## 请参阅  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)