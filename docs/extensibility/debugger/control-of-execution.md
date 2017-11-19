---
title: "控制执行 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79d888e9b50d18b4a9d46a8914381db27f09698d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="control-of-execution"></a>控制执行
调试引擎 (DE) 通常情况下发送以下事件之一作为最后的启动事件：  
  
-   入口点事件，如果将连接到新启动程序  
  
-   加载完成事件，如果附加到已在运行的程序  
  
 这两个这些事件包括停止事件，这意味着，DE 等待响应来自用户通过 IDE。 有关详细信息，请参阅[运行模式](../../extensibility/debugger/operational-modes.md)。  
  
## <a name="stopping-event"></a>停止事件  
 当停止事件发送到调试会话：  
  
1.  可以从事件接口获得程序和包含当前指令指针的线程。  
  
2.  IDE 确定的当前源代码文件和位置，该位置它显示在编辑器中突出显示。  
  
3.  调试会话通常对应于此第一个停止事件通过调用程序的**继续**方法。  
  
4.  程序，然后运行，直到它遇到停止条件，例如命中的断点，在其中用例 DE 断点将事件发送到调试会话。 断点事件是一个停止事件中，且 DE 再次等待用户响应。  
  
5.  如果用户选择进入并单步超过，或从函数，IDE 将提示调试会话才能调用程序的`Step`方法，将其传递的步骤 （指令、 语句或行） 和步骤的类型的单位-即，是否进入并单步，超过或跳出函数。 步骤完成后，DE 将发送到调试会话，即停止事件的步骤完成事件。  
  
     - 或 -  
  
     如果用户选择继续执行当前指令指针从，IDE 会提示调试会话才能调用程序的**执行**方法。 程序继续执行，直到遇到下一个停止条件。  
  
     - 或 -  
  
     调试会话调试会话是忽略特定 stopping 事件，如果调用程序的**继续**方法。 如果它遇到停止条件时，程序已逐句执行、 逐过程执行或跳出函数，则它继续步骤。  
  
 以编程方式，当 DE 遇到停止条件时，它将发送作为此类停止事件[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)到会话调试管理器 (SDM) 的方式[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)接口。 DE 传递[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)和[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)表示的程序和包含当前指令指针的线程的接口。 SDM 调用[IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)若要获取的顶级堆栈帧和调用[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)若要获取与当前指令关联的文档上下文指针。 此文档上下文通常是源代码文件名称、 行和列号。 IDE 使用上述属性突出显示包含当前指令指针的源代码。  
  
 SDM 通常对应于此第一个停止事件通过调用[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 然后程序将运行，直到它遇到停止条件，例如命中的断点，用例 DE 将发送[IDebugBreakpointEvent2 接口](../../extensibility/debugger/reference/idebugbreakpointevent2.md)到 SDM。 断点事件是一个停止事件中，且 DE 再次等待用户响应。  
  
 如果用户选择进入并单步超过，或从函数，IDE 将提示 SDM 调用[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)，将其传递[STEPUNIT](../../extensibility/debugger/reference/stepunit.md) （指令、 语句或行） 和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)，即，是否要单步执行、 逐过程执行或跳出函数。 步骤完成后，将发送 DE [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) SDM，即停止事件的接口。  
  
 如果用户选择继续执行当前指令指针从，IDE 会询问 SDM 调用[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)。 程序继续执行，直到遇到下一个停止条件。  
  
 如果调试包，若要忽略特定的停止事件调试包调用 SDM，后者将调用[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 如果它遇到停止条件时，程序已逐句执行、 逐过程执行或跳出函数，则它继续步骤。 这意味着，程序要维护的单步执行的状态，这样就知道如何继续进行操作。  
  
 SDM 对的调用`Step`，**执行**，和**继续**是异步的这意味着 SDM 需要调用迅速返回。 如果 DE 发送 SDM stopping 事件之前在同一线程`Step`，**执行**，或**继续**返回，SDM 挂起。  
  
## <a name="see-also"></a>另请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)