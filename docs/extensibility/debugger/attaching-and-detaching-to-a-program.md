---
title: "附加和分离到一个程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "附加到程序的调试引擎"
  - "调试引擎，与程序分离"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 附加和分离到一个程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

附加调试器需要发送方法和事件正确的顺序与相应的属性。  
  
## 方法和事件的顺序  
  
1.  会议调试管理器 \(SDM\)调用 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。  
  
     基于调试引擎 \(DE\)处理模型， `IDebugProgramNodeAttach2::OnAttach` 方法返回下列方法之一，确定了接下来发生的情况。  
  
     如果 `S_FALSE` 返回，调试引擎成功附加到程序。  否则， [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 方法调用完成额外处理。  
  
     如果 `S_OK` 返回， DE 将加载在同一进程作为 SDM。  SDM 执行以下任务:  
  
    1.  调用 [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 获取 DE 的引擎信息。  
  
    2.  用于共同创建 DE。  
  
    3.  调用 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
2.  DE 发送 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 到 `EVENT_SYNC` 属性的 SDM。  
  
3.  DE 发送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 到 `EVENT_SYNC` 属性的 SDM。  
  
4.  DE 发送 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 到 `EVENT_SYNC_STOP` 属性的 SDM。  
  
 分离程序很简单，过程分为两步，如下所示:  
  
1.  SDM 调用 [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md)。  
  
2.  DE 发送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)