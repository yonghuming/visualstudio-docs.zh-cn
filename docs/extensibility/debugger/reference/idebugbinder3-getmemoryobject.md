---
title: "IDebugBinder3::GetMemoryObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetMemoryObject"
helpviewer_keywords: 
  - "IDebugBinder3::GetMemoryObject 方法"
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetMemoryObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法检索表示内存对象的内存此对象绑定。  
  
## 语法  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### 参数  
 `pField`  
 \[in\] 指定哪些字段访问对象的内存。  
  
 `uConstant`  
 \[in\] 表示一个内存地址或值常数值的。  
  
 `ppObject`  
 \[out\] 表示内存的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 此对象绑定。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)