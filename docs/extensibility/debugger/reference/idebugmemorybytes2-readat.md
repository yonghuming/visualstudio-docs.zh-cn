---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::ReadAt 方法"
  - "ReadAt 方法"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

读取字节序列，开始在特定位置。  
  
## 语法  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### 参数  
 `pStartContext`  
 \[in\] 在指定位置开始读取字节的 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 对象。  
  
 `dwCount`  
 \[in\] 读取的字节数。  并指定 `rgbMemory` 数组的长度。  
  
 `rgbMemory`  
 \[in, out\] 用字节填充的数组实际读取。  
  
 `pdwRead`  
 \[out\] 返回实际读取的连续字节的数目。  
  
 `pdwUnreadable`  
 \[in, out\] 返回不可读取的字节数。  ，如果客户端不可读的字节，数不感兴趣的长度可为 null 值。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 如果 100 个字节请求，并前 50 可读的，下 20 不可读的，因此，余下的 30 可读的，此方法返回:  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 在这种情况下，，因为 `*pdwRead + *pdwUnreadable < dwCount`，调用方必须另外调用读取必须被 70 高级请求的剩余的 30 个字节原始 100 中和 `pStartContext` 参数传递的 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 对象。  
  
## 请参阅  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)