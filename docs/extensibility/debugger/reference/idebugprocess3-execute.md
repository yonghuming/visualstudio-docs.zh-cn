---
title: "IDebugProcess3::Execute | Microsoft Docs"
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
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

继续运行此从一种状态中止处理。  \(例如步骤\) 清除所有以前执行状态和处理再次开始执行。  
  
> [!NOTE]
>  应使用此方法而不是 [执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。  
  
## 语法  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### 参数  
 `pThread`  
 \[in\] 表示线程的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象执行。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 当用户开始执行从其他某种进程的线程中的一种停止状态，此方法调用此过程。  ，当用户选择 **开始** 命令在 IDE 时，的 **调试** 菜单此方法被调用。  此方法的实现可能十分简单调用当前线程的 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 方法在处理。  
  
> [!WARNING]
>  不要将一个终止的事件或一个即时 \(\) 同步事件。 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ，当处理此时调用，否则调试器会停止。  
  
## 请参阅  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)