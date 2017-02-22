---
title: "启动调试器 | Microsoft Docs"
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
  - "调试 [调试 SDK]，启动调试器"
  - "启动调试器 [调试 SDK]"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 启动调试器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

启动调试器需要发送方法和事件正确的顺序与其相应的属性。  
  
## 方法和事件的顺序  
  
1.  会议调试管理器 \(SDM\)通过选择 **调试** 菜单，然后选择 **启动**调用。  有关更多信息，请参见[下启动程序](../../extensibility/debugger/launching-a-program.md)。  
  
2.  SDM 调用 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。  
  
3.  基于调试引擎 \(DE\)处理模型， `IDebugProgramNodeAttach2::OnAttach` 方法返回下列方法之一，确定了接下来发生的情况。  
  
     如果 `S_FALSE` 返回，调试引擎 \(DE\)会在虚拟机的过程中加载。  
  
     \- 或 \-  
  
     如果 `S_OK` 返回， DE 将在 SDM 的过程中加载。  SDM 然后执行以下任务:  
  
    1.  调用 [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 获取 DE 的引擎信息。  
  
    2.  用于共同创建 DE。  
  
    3.  调用 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
4.  DE 发送 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 到 `EVENT_SYNC` 属性的 SDM。  
  
5.  DE 发送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 到 `EVENT_SYNC` 属性的 SDM。  
  
6.  DE 发送 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 到 `EVENT_SYNC` 属性的 SDM。  
  
7.  DE 发送 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 到 `EVENT_SYNC` 属性的 SDM。  
  
8.  DE 发送 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 到 `EVENT_SYNC` 属性的 SDM。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)   
 [下启动程序](../../extensibility/debugger/launching-a-program.md)