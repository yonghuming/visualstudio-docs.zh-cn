---
title: "IDebugBinder::ResolveRuntimeType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveRuntimeType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveRuntimeType 方法"
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法确定对象的运行时类型。  
  
## 语法  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```c#  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### 参数  
 `pObject`  
 \[in\] 要解决的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 。  
  
 `ppResolved`  
 \[out\] 返回对象的类型作为 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 对象的运行时类型总是在编译时未知。  例如，使用，多态性，参数传递到函数作为其基类，例如 button 类。  实参可能是派生类，如单选按钮类。  
  
## 请参阅  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)