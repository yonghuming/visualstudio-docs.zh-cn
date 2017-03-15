---
title: "IDebugThread2::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

继续执行线程。  
  
## 语法  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### 参数  
 `pdwSuspendCount`  
 \[out\] 在继续操作之后返回挂起计数。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 每个调用此方法时挂起计数，直到其达到 0，此时，执行实际上还原。  这在 **线程** 挂起计数显示调试窗口。  
  
 对于每次调用此方法，必须了解以前的调用 [挂起](../Topic/IDebugThread2::Suspend.md) 方法。  挂起计数确定到目前为止多少次 `IDebugThread2::Suspend` 方法调用。  
  
## 请参阅  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [挂起](../Topic/IDebugThread2::Suspend.md)