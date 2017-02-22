---
title: "控件事件 | Microsoft Docs"
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
  - "调试 [调试 SDK] 事件"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 控件事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

必须在程序中控制执行发送事件。  所有事件发送使用 [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) 接口并具有需要执行 [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) 方案的属性。  
  
## 其他方法  
 某些操作需要其他方法的实现，如下所示:  
  
-   发送 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 接口，当调试引擎 \(DE\)初始化时需要执行 [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) 方法。  
  
-   执行控件实现这样的控件事件与 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) 和[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 接口。  **IDebugBreakEvent2** 对于异步仅中断是必需的。  
  
-   单步执行函数需要 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 接口及其方法的实现。  
  
 从派生断点的操作需要 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 接口，以及 [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 和 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 方法的实现。  
  
 异步计算表达式需要执行 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 接口及其 [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[并 GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 方法。  
  
 同步操作需要执行 [IDebugEngine2:: ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) 方法。  
  
 对于字符串写入样式输出的引擎，必须执行 [IDebugOutputStringEvent2:: GetString](../Topic/IDebugOutputStringEvent2::GetString.md) 方法。  
  
## 请参阅  
 [执行控制和状态评估](../../extensibility/debugger/execution-control-and-state-evaluation.md)