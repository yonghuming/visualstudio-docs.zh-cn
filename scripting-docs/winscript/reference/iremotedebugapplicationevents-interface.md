---
title: "IRemoteDebugApplicationEvents 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents 接口"
ms.assetid: 9626519e-910c-48e0-ae99-c711ce6628fd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents 接口
`IRemoteDebugApplicationEvents` 接口是调试应用程序提供的事件接口。  此接口始终调用从调试器线程内。  
  
 除了从 `IUnknown` 继承的方法之外，`IRemoteDebugApplicationEvents` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IRemoteDebugApplicationEvents::OnConnectDebugger](../../winscript/reference/iremotedebugapplicationevents-onconnectdebugger.md)|处理调试器连接事件。|  
|[IRemoteDebugApplicationEvents::OnDisconnectDebugger](../../winscript/reference/iremotedebugapplicationevents-ondisconnectdebugger.md)|处理调试器断开事件。|  
|[IRemoteDebugApplicationEvents::OnSetName](../../winscript/reference/iremotedebugapplicationevents-onsetname.md)|处理一个set名称的事件。|  
|[IRemoteDebugApplicationEvents::OnDebugOutput](../../winscript/reference/iremotedebugapplicationevents-ondebugoutput.md)|处理调试器输出事件。|  
|[IRemoteDebugApplicationEvents::OnClose](../../winscript/reference/iremotedebugapplicationevents-onclose.md)|处理应用程序关闭事件。|  
|[IRemoteDebugApplicationEvents::OnEnterBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onenterbreakpoint.md)|处理输入的断点一个事件。|  
|[IRemoteDebugApplicationEvents::OnLeaveBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onleavebreakpoint.md)|处理保留的断点一个事件。|  
|[IRemoteDebugApplicationEvents::OnCreateThread](../../winscript/reference/iremotedebugapplicationevents-oncreatethread.md)|处理创建线程活动。|  
|[IRemoteDebugApplicationEvents::OnDestroyThread](../../winscript/reference/iremotedebugapplicationevents-ondestroythread.md)|处理一个线程销毁的事件。|  
|[IRemoteDebugApplicationEvents::OnBreakFlagChange](../../winscript/reference/iremotedebugapplicationevents-onbreakflagchange.md)|处理事件，发生重大更改标志。|