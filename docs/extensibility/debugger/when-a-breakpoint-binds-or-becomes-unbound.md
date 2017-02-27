---
title: "当断点绑定或将成为绑定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，断点之间的绑定事件"
  - "断点绑定事件"
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 当断点绑定或将成为绑定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当断点不能在则必须调用该 [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 方法，绑定时间，并创建断点的时间都不同。  
  
## 调用的方法  
 会议调试管理器 \(SDM\)调用下列方法:  
  
1.  [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)。  DE 返回 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)。  
  
2.  [IDebugPendingBreakpoint2:: 启用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)。  
  
3.  [IDebugPendingBreakpoint2:: 活动](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)。  
  
4.  [IDebugPendingBreakpoint2:: 绑定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 方法并返回 S\_OK。  DE 发送 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 或 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)。  
  
5.  验证的[IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 和 [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 方法并获取绑定断点。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)