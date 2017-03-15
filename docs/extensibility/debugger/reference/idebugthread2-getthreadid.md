---
title: "IDebugThread2::GetThreadId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetThreadId"
helpviewer_keywords: 
  - "IDebugThread2::GetThreadId"
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取系统线程标识符。  
  
## 语法  
  
```cpp#  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```c#  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### 参数  
 `pdwThreadId`  
 \[out\] 返回系统线程标识符。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 线程 ID 用于标识在其他线程中的线程在处理。  
  
## 示例  
 下面的示例演示如何执行简单的 `CProgram` 对象的方法实现 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 接口。  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## 请参阅  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)