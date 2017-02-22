---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)用于此接口发送调试事件设置为会话调试管理器 \(SDM\)。  
  
## 语法  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## 实现者说明  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 实现此接口接收调试引擎的事件。  
  
## 调用方的说明  
 ，当 SDM 调用 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)或 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)时，调试引擎通常接收此接口。  调试引擎事件发送到 SDM 通过调用 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugEventCallback2`方法。  
  
|方法|说明|  
|--------|--------|  
|[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|发送调试事件通知到 SDM。|  
  
## 备注  
 虽然 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 和 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 指定它们接受 `IDebugEventCallback2` 接口，则并非如此，并且，接口指针将始终为 null 值。  相反，调试引擎在调用必须使用 `IDebugEventCallback2` 接口接收到 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)或 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
 如果包实现托管代码的 [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) ，强烈建议 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 在传递到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)的各种接口调用。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)