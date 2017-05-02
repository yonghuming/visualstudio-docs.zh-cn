---
title: "IDebugApplicationThreadEvents110 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThreadEvents110 接口"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThreadEvents110 接口
添加多个线程操作。  这些事件仅本地。  即可以订阅只能在使用 [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) 建议进行调试，处理，并在PDM应用程序的unadvise方法线程对象\(实现 [IDebugApplicationThread 接口](../../winscript/reference/idebugapplicationthread-interface.md)\)的对象。  它们在线程上执行这些来源。  
  
> [!IMPORTANT]
>  此接口由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 方法  
 `IDebugActivationThreadEvents110` 接口公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|调用使用PDM的线程切换线程中启动。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|线程从断点还原，并再次处于活动状态。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|线程对断点挂起和可以调用线程完全挂起的处理调用。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|调用使用PDM的线程切换线程中完成。|