---
title: "IDebugFunctionObject::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::Evaluate"
helpviewer_keywords: 
  - "IDebugFunctionObject::Evaluate 方法"
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调用函数并返回得到的值为对象。  
  
## 语法  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### 参数  
 `ppParams`  
 \[in\] 数组表示输入参数的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象。  这些参数的每一个用一个 `Create` 方法创建了 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 接口。  
  
 `dwParams`  
 \[in\] 的参数数量。 `ppParams` 数组。  
  
 `dwTimeout`  
 \[in\] 以毫秒为单位指定最长时间，因此，在返回等待来自此方法。  使用 `INFINITE` 会无限期地等待。  
  
 `ppResult`  
 \[out\] 返回表示函数的值 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 为对象。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 此方法设置并执行调用 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 对象表示的功能。  
  
## 请参阅  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)