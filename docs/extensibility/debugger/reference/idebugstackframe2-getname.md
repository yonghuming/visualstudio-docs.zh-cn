---
title: "IDebugStackFrame2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetName"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetName"
ms.assetid: 069d4f96-363f-404e-9c89-5318c4c9821b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取堆栈帧的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName (   
   out string pbstrName  
);  
```  
  
#### 参数  
 `pbstrName`  
 \[out\] 返回堆栈帧的名称。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 堆栈帧的名称通常是所执行的方法的名称。  
  
## 请参阅  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)