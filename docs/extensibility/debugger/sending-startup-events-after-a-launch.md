---
title: "在启动之后发送启动事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0620821ec908deed2c57ddfefb40763a48fd2074
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sending-startup-events-after-a-launch"></a>在启动之后发送启动事件
一旦的调试引擎 (DE) 附加到程序时，会将一系列启动事件发送回调试会话。  
  
 启动事件发送回调试会话如下所示：  
  
-   引擎创建事件。  
  
-   程序创建事件。  
  
-   线程创建和模块加载事件。  
  
-   加载完成事件，发送的代码时加载和准备好运行，但在执行任何代码之前  
  
    > [!NOTE]
    >  此事件将继续运行，初始化全局变量，并且启动例程运行。  
  
-   可能的其他线程创建和模块加载事件。  
  
-   用信号通知程序已达到其主入口点，如的入口点事件**Main**或`WinMain`。 此事件通常不发送如果 DE 将附加到已在运行程序。  
  
 以编程方式，DE 第一次发送会话调试管理器 (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)接口，它表示引擎创建事件后, 跟[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)表示程序创建事件。  
  
 这通常跟一个或多个[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)线程创建事件和[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)模块加载事件。  
  
 当代码已加载并准备好运行，但在执行任何代码之前，DE 发送 SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)负载完成事件。 最后，如果程序尚未运行，则 DE 会发送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)入口点事件，信号发送程序已达到其主入口点，并且随时可供调试。  
  
## <a name="see-also"></a>另请参阅  
 [控制执行](../../extensibility/debugger/control-of-execution.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)