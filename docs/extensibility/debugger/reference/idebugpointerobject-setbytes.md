---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::SetBytes 方法"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

将值设置为指向自一系列连续的字节。  
  
## 语法  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### 参数  
 `dwStart`  
 \[in\] 偏移量，在字节，对象从开始点。  
  
 `dwCount`  
 \[in\] 设置的字节数。  
  
 `pBytes`  
 \[in\] 表示新值的字节。  此值存储到对象，开始在给定的偏移量。  
  
 `pdwBytes`  
 \[out\] 返回实际设置的字节数。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 使用此方法，如果指针如由以下 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 指向基元类型或简单的某些基元类型 \(即可由字节一个简单的序列表示\) 的数组。  此 `IDebugPointerObject` 对象不能为 null 引用 \(它必须指向内存中的地址\)。  
  
## 请参阅  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)