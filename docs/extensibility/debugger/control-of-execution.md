---
title: "控制执行 | Microsoft Docs"
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
  - "调试 [调试 SDK]，控制执行"
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 控制执行
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)通常发送以下操作之一为最后一启动操作:  
  
-   入口点事件，因此，如果附加到新的启动程序  
  
-   加载完成事件，因此，如果附加到已经运行的程序  
  
 这两个事件终止事件，这意味着 DE 通过 IDE 等待来自用户的响应。  有关更多信息，请参见 [操作状态](../../extensibility/debugger/operational-modes.md)。  
  
## 停止事件  
 当一个停止点的事件发送到调试会话:  
  
1.  包含当前指令指针的过程和线程可以从事件接口获取。  
  
2.  IDE 确定当前源代码文件和位置，它在编辑器中显示。  
  
3.  调试会话通常响应第一个停止点的事件通过调用程序的 **继续** 方法。  
  
4.  然后程序运行，直到遇到一种停止状态，如命中了断点，，在 DE 断点事件发送到调试会话情况下。  断点事件是一个停止点的事件，并且， DE 重新等待用户响应。  
  
5.  如果用户决定单步执行，在中，或在函数之外， IDE 提示调试会话调用过程的 `Step` 方法，并单元步骤 \(命令、语句或行\) 和类型步骤是，是否单步执行，在中，或在函数之外。  当该步骤完成后，、发送步骤完成事件。调试会话，这是一个停止点的事件。  
  
     \- 或 \-  
  
     如果用户决定继续执行从当前指令指针， IDE 提示调试会话调用过程的 **执行** 方法。  程序继续执行，直到遇到的下一个停止状态。  
  
     \- 或 \-  
  
     如果调试会话是忽略特定终止的事件，调试会话调用过程的 **继续** 方法。  如果程序单步执行，在中，或在函数之外，在遇到这种停止状态，则扩展该步骤。  
  
 编程，那么，当 DE 遇到一种停止状态时，它发送作为 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 为会话通过 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 接口调试管理器 \(SDM\)这样的终止的事件。  DE 将表示包含当前指令指针的过程和线程的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 和 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 接口。  SDM 调用 [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 获取顶部堆栈帧并调用 [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 获取文档上下文与当前指令指针。  文档上下文通常是源代码文件名、行号和列号。  IDE 使用这些显示包含当前指令指针的源代码。  
  
 SDM 通常响应第一个停止点的事件通过调用 [IDebugProgram2:: 继续](../../extensibility/debugger/reference/idebugprogram2-continue.md)。  然后程序运行，直到遇到一种停止状态，如命中了断点，，在 DE 发送 [IDebugBreakpointEvent2 接口](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 到 SDM 情况下。  断点事件是一个停止点的事件，并且， DE 重新等待用户响应。  
  
 如果用户决定单步执行，在中，或在函数之外， IDE 是否提示 SDM 调用 [IDebugProgram2:: 步骤](../../extensibility/debugger/reference/idebugprogram2-step.md)，将 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) \(命令、语句或行\) 和 [STEPKIND](../../extensibility/debugger/reference/stepkind.md)，也就是说，单步执行，在中，或在函数之外。  当该步骤完成后，、发送一 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 接口到 SDM，是一个停止点的事件。  
  
 如果用户决定继续执行从当前指令指针， IDE 请求 SDM 调用 [IDebugProgram2:: 执行](../../extensibility/debugger/reference/idebugprogram2-execute.md)。  程序继续执行，直到遇到的下一个停止状态。  
  
 如果调试包是忽略特定终止的事件，调试打包名为 SDM，调用 [IDebugProgram2:: 继续](../../extensibility/debugger/reference/idebugprogram2-continue.md)。  如果程序单步执行，在中，或在函数之外，在遇到这种停止状态，则扩展该步骤。  这意味着程序维护一个单步执行状态，因此，它会继续。  
  
 调用 SDM 对 `Step`， **执行**，并且， **继续** 是异步的，这意味着， SDM 希望调用尽快返回。  如果 DE 发送 SDM 中的一个停止点的事件。 `Step`， **执行**之前的相同线程或 **继续** 返回， SDM 停止。  
  
## 请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)