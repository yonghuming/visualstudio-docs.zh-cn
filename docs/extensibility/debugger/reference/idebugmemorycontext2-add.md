---
title: "IDebugMemoryContext2::Add | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Add"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Add 方法"
  - "Add 方法"
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

添加指定值到当前上下文并返回新上下文。  
  
## 语法  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### 参数  
 `dwCount`  
 \[in\] 要添加的值到当前上下文。  
  
 `ppMemCxt`  
 \[out\] 返回一个新的 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 内存上下文是地址，因此，将值添加到地址将导致请求新的上下文接口的新地址。  
  
 此方法必须总是生成新的上下文，因此，即使该发生的地址是在内存空间以外与此上下文。  此唯一的例外是，如果内存不能用于新上下文分配，或者 `ppMemCxt` 是错误\) 的 null 值 \(\)。  
  
## 请参阅  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)