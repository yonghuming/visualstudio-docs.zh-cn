---
title: "支持的事件类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b05ff310a2e0c478b6f9be766f27731ca9f8f9ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="supported-event-types"></a>支持的事件类型
Visual Studio 调试当前支持以下事件类型：  
  
-   异步事件  
  
     通知会话调试管理器 (SDM) 和正在调试的应用程序的状态将更改的 IDE。 SDM 和 IDE 的空闲处理这些事件。 处理该事件后，未回复发送到的调试引擎 (DE) 中。 [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)和[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)接口是异步事件的示例。  
  
-   同步事件  
  
     通知的 SDM 和正在调试的应用程序的状态将更改的 IDE。 这些事件和异步事件的唯一区别在于，通过发送答复[ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)方法。  
  
     发送一个同步事件是需要你 DE 以便继续处理后 IDE 接收和处理事件的情况下很有用。  
  
-   同步的停止事件，或停止事件  
  
     通知 SDM 和 IDE 正在调试的应用程序已停止执行代码。 如果要将停止事件发送该方法通过[事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)、 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)参数是必需的。 正在停止事件继续通过调用以下方法之一：  
  
    -   [执行](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     接口[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)是停止事件的示例。  
  
    > [!NOTE]
    >  不支持异步停止事件。 它是错误发送异步停止事件。  
  
## <a name="discussion"></a>讨论  
 事件的实际实现取决于你 DE 的设计。 发送每个事件的类型由其属性，当您设计 DE 设置确定。 例如，可能会发送一个 DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)为异步事件，而另一个可能会向它发送为停止事件。  
  
 下表指定哪些程序和线程参数所需的事件，以及事件类型。 任何事件可以是同步的。 要同步的任何事件不要求。  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md)界面是必需的所有事件。  
  
|Event|IDebugProgram2|IDebugThread2|停止事件|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必需|必需|是|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必需|必需|是|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必需|必需|No|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不允许|不允许|No|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不允许|不允许|No|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必需|必需|是|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|允许，但并不是必需|允许，但并不是必需|可以|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必需|必需|是|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|允许，但并不是必需|允许，但并不是必需|可以|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必需|必需|是|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必需|必需|是|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|允许，但并不是必需|允许，但并不是必需|可以|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必需|允许，但并不是必需|No|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必需|允许，但并不是必需|No|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必需|允许，但并不是必需|No|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必需|允许，但并不是必需|No|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必需|允许，但并不是必需|No|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
|IDebugStopCompleteEvent2|必需|必需|是|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必需|必需|是|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必需|必需|No|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必需|必需|No|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|允许，但并不是必需|允许，但并不是必需|No|  
  
## <a name="see-also"></a>另请参阅  
 [发送事件](../../extensibility/debugger/sending-events.md)