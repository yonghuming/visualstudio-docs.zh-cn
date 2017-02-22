---
title: "支持的事件类型 | Microsoft Docs"
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
  - "调试 [调试 SDK]，受支持的事件"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 支持的事件类型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当前调试的 Visual Studio 支持以下事件类型:  
  
-   异步操作  
  
     通知会话调试管理器 \(SDM\)和 IDE 正在调试的应用程序状态的更改。  这些事件处理在 SDM 和 IDE 中有空时。  ，在事件处理，答案不会发送到调试引擎 \(DE\)。  [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) 和 [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) 接口是异步操作的示例。  
  
-   同步事件  
  
     通知 SDM 和 IDE 正在调试的应用程序状态的更改。  在这些事件和异步事件之间的唯一区别是答案通过 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) 方法发送。  
  
     ，如果需要 DE 继续处理在 IDE 后接收和处理事件，并发送一个同步事件非常有用。  
  
-   同步终止的事件或停止事件  
  
     通知 SDM 和 IDE 正在调试的应用程序停止执行代码。  当通过方法 [事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)时发送一个停止点的事件，需要 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 参数。  停止事件通过调用继续到一个下列方法:  
  
    -   [执行](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [单步执行](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [继续](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     接口 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 和 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 是停止事件的示例。  
  
    > [!NOTE]
    >  异步终止的事件不受支持。  它是发送异步终止的事件的错误。  
  
## 讨论  
 事件的实际实现取决于 DE 的模型。  其属性取决于发送的每个事件的类型，设置，当您设计、时。  例如，在中，而另一个可发送为一个停止点的事件，一个 DE 可以发送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 作为异步操作。  
  
 下表指定要程序和线程参数需要事件\)，以及事件。  所有事件可以是同步的。  事件不需要同步。  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) 接口对于所有事件是必需的。  
  
|Event|IDebugProgram2|IDebugThread2|停止事件|  
|-----------|--------------------|-------------------|----------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|允许，但是，不需|允许，但是，不需|否|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必需|必需|是|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|允许，但是，不需|允许，但是，不需|否|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|允许，但是，不需|允许，但是，不需|否|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|允许，但是，不需|允许，但是，不需|否|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必需|必需|是|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必需|必需|否|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不允许|不允许|否|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不允许|不允许|否|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必需|必需|是|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|允许，但是，不需|允许，但是，不需|可以是|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必需|必需|是|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|允许，但是，不需|允许，但是，不需|可以是|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必需|必需|是|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必需|必需|是|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|允许，但是，不需|允许，但是，不需|可以是|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必需|允许，但是，不需|否|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|允许，但是，不需|允许，但是，不需|否|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必需|允许，但是，不需|否|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必需|允许，但是，不需|否|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必需|允许，但是，不需|否|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必需|允许，但是，不需|否|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|允许，但是，不需|允许，但是，不需|否|  
|IDebugStopCompleteEvent2|必需|必需|是|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必需|必需|是|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|允许，但是，不需|允许，但是，不需|否|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必需|必需|否|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必需|必需|否|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|允许，但是，不需|允许，但是，不需|否|  
  
## 请参阅  
 [发送事件](../../extensibility/debugger/sending-events.md)