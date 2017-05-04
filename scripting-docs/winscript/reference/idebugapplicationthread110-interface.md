---
title: "IDebugApplicationThread110 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110 接口"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThread110 接口
为 [IDebugApplicationThread 接口](../../winscript/reference/idebugapplicationthread-interface.md) 接口提供更多功能。  
  
> [!IMPORTANT]
>  此接口由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 方法  
 `IDebugApplicationThread110` 接口公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|在主线程进行异步调用。|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|计数多少线程从PDM的线程切换结构的请求当前进程。  通常为0或1，但是，它可以才会较高，如果一个线程调用过程的开头，但例如同步调用线程或挂起线程的触发器\(，通过触发在调试器线程问题\)的IDebugApplicationEvents事件|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) 在此线程和尚未完成。|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|此线程可以处理调用使用PDM的线程切换结构的状态\(例如SynchronousCallInThread\)。|