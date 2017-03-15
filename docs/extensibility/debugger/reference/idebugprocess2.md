---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "IDebugProcess2 接口"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示运行在端口的过程。  如果端口是本地的端口，则 `IDebugProcess2` 在本地计算机上通常表示物理过程。  
  
## 语法  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## 实现者说明  
 此接口由自定义端口提供程序实现托管程序作为组。  必须由端口提供程序实现此接口。  
  
 ，如果它支持启动程序通过 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)，调试引擎还实现此接口。  
  
## 调用方的说明  
 此接口主要由该会话调用调试管理器 \(SDM\)为了在中标识程序的一组进程交互。  
  
 调用 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) 或 [GetProcess](../Topic/IDebugPort2::GetProcess.md) 获取此接口。  此接口通过调用 `IDebugEngineLaunch2::LaunchSuspended`也会返回。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProcess2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|获取处理的说明。|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|枚举中包含的处理程序。|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|获取处理的标题、友好名称或文件名。|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|获取此过程运行的计算机服务器的实例。|  
|[终止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|终止进程。|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|附加到进程。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|确定 SDM 是否可以分离进程。|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|与进程分离的调试器。|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|获取系统进程标识符。|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|获取此的全局唯一标识符 \(guid\) 处理。|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[已弃用\]|获取调试进程内会话的名称。<br /><br /> \[已弃用。  应始终返回 `E_NOTIMPL`。\]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|枚举运行进程中的线程。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|请求运行代码中的下处理程序终止。|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|获取此过程运行的端口。|  
  
## 备注  
 `IDebugProcess2` 包含一个或多 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口。  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../Topic/IDebugPort2::GetProcess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)