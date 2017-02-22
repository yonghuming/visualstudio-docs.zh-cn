---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::GetBytes 方法"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取一个值指向作为一系列连续的字节。  
  
## 语法  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### 参数  
 `dwStart`  
 \[in\] 偏移量，在字节，对象从开始点。  
  
 `dwCount`  
 \[in\] 检索的字节数。  
  
 `pBytes`  
 \[in, out\] 使用该值填充为一系列连续的字节数组，开始在从对象的给定的偏移量点。  
  
 `pdwBytes`  
 \[out\] 返回实际检索的字节数。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 使用此方法，如果指针如由以下 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 指向基元类型或简单的某些基元类型 \(即可由字节一个简单的序列表示\) 的数组。  
  
## 请参阅  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)