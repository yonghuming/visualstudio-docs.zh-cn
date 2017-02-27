---
title: "IDebugProgram2::GetMemoryBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索程序所占用的内存中字节数组。  
  
## 语法  
  
```cpp#  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### 参数  
 `ppMemoryBytes`  
 \[out\] 返回表示程序的内存中字节数组的 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 内存中字节数组如由 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 对象是为内存和未分配的任何内存的程序的图像，当程序已执行。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)