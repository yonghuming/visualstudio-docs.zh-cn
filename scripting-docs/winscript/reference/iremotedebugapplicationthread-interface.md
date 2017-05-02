---
title: "IRemoteDebugApplicationThread 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread 接口"
ms.assetid: 062bb997-7b9e-4945-bfbe-d5b92d5cb707
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplicationThread 接口
表示执行线程在特定应用程序中。  
  
 除了从 `IUnknown` 继承的方法之外，`IRemoteDebugApplicationThread` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IRemoteDebugApplicationThread::GetSystemThreadId](../../winscript/reference/iremotedebugapplicationthread-getsystemthreadid.md)|返回运行与系统有关的标识符与线程关联。|  
|[IRemoteDebugApplicationThread::GetApplication](../../winscript/reference/iremotedebugapplicationthread-getapplication.md)|返回应用程序对象与该线程。|  
|[IRemoteDebugApplicationThread::EnumStackFrames](../../winscript/reference/iremotedebugapplicationthread-enumstackframes.md)|返回堆栈帧的枚举数与该线程。|  
|[IRemoteDebugApplicationThread::GetDescription](../../winscript/reference/iremotedebugapplicationthread-getdescription.md)|获取此线程声明和状态。|  
|[IRemoteDebugApplicationThread::SetNextStatement](../../winscript/reference/iremotedebugapplicationthread-setnextstatement.md)|延续的强制尽可能接近特定代码上下文，在特定框架中。|  
|[IRemoteDebugApplicationThread::GetState](../../winscript/reference/iremotedebugapplicationthread-getstate.md)|获取此线程的状态。|  
|[IRemoteDebugApplicationThread::Suspend](../../winscript/reference/iremotedebugapplicationthread-suspend.md)|挂起线程。|  
|[IRemoteDebugApplicationThread::Resume](../../winscript/reference/iremotedebugapplicationthread-resume.md)|继续执行线程。|  
|[IRemoteDebugApplicationThread::GetSuspendCount](../../winscript/reference/iremotedebugapplicationthread-getsuspendcount.md)|返回线程的挂起计数。|