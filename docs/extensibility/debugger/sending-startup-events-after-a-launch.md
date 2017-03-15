---
title: "发送应用程序启动后启动事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，启动事件"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 发送应用程序启动后启动事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

一次调试引擎 \(DE\)附加到程序，它将一系列操作添加到启动调试会话。  
  
 启动事件发送回调试会话包括:  
  
-   引擎创建事件。  
  
-   程序创作事件。  
  
-   线程的创建和模块加载事件。  
  
-   加载完成事件，发送代码改动是加载并准备，但是，， " 所有代码前  
  
    > [!NOTE]
    >  当此事件继续时，全局变量初始化，并启动实例上运行。  
  
-   可以其他线程的创建和模块加载事件。  
  
-   入口点事件，信号程序已到达其的主入口点，例如 **主** 或 `WinMain`。  通常不发送此事件，如果 DE 附加到正在运行的程序。  
  
 编程方式， DE 首先将会话调试 \(SDM\) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 接口，表示引擎创建操作，则 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)遵循，表示程序创作事件管理器的。  
  
 这是由一个或多 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 线程创建事件和 [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 模块加载事件通常执行。  
  
 如果代码是加载并准备时，但是，， " 所有代码前， DE 发送 SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 加载完成事件。  最后，因此，如果程序尚未运行， DE 发送 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 入口点事件，指示程序已到达其的主入口点并准备调试。  
  
## 请参阅  
 [控制执行](../../extensibility/debugger/control-of-execution.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)