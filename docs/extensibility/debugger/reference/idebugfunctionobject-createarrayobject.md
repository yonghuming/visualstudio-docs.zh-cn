---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateArrayObject 方法"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建数组对象。  此数组可能包含原始或对象实例值。  
  
## 语法  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### 参数  
 `ot`  
 \[in\] 指定从一个数组对象的类型 [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) 枚举的值。  
  
 `pClassField`  
 \[in\] 表示对象的类 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象，因此，如果创建对象实例值。  如果创建一组原始对象，此参数是一个 null 值。  
  
 `dwRank`  
 \[in\] 数组维度的级别或数量。  
  
 `dwDims`  
 \[in\] 数组每一维的大小。  
  
 `dwLowBounds`  
 \[in\] 每个维度的源 \(通常为 0 或 1\)。  
  
 `ppObject`  
 \[out\] 返回表示该新创建的数组的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象。  这实际上是 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) 对象。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 调用此方法创建表示数组参数传递给函数的 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 接口表示的对象。  
  
## 请参阅  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)