---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

是否通知调试引擎 \(DE\)在当前代码位置停止或继续执行。  
  
## 语法  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### 参数  
 `fCanStop`  
 \[in\] 非零 \(`TRUE`\)，如果 DE 应在当前代码位置停止;否则，零 \(0\)`FALSE`\)。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此事件的接收方通常会调用 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md) 方法确定 DE 终止的原因，然后调用与相应的响应的 `IDebugCanStopEvent2::CanStop` 方法。  
  
 如果 DE 停止，它发送描述终止原因的事件。  通常有发送的两个事件， [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 接口或信号中断表示用户和 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 接口表示的断点事件。  
  
## 请参阅  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)