---
title: "发送所需的事件 | Microsoft Docs"
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
  - "调试 [调试 SDK]，需要的事件"
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 发送所需的事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

用于将所需的事件使用此方法。  
  
## 用于将所需的事件处理  
 以下事件按此顺序，需要，那么，当创建调试引擎 \(DE\)并将其附加到程序中:  
  
1.  ，当 DE 用于调试进程中，的一个或多个过程初始化请发送到会议的一 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 事件对象调试管理器 \(SDM\)。  
  
2.  当要调试的程序附加到时，请发送到 SDM 的一 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件对象。  此操作可能是一个停止点的事件，根据引擎模型。  
  
3.  如果程序附加到，在进程启动时，请发送到 SDM 的一 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 事件对象通知新线程的 IDE。  此操作可能是一个停止点的事件，根据引擎模型。  
  
4.  请发送到 SDM 的一 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 事件对象，而正在调试的程序完成加载或时，当附加到程序完成。  此事件必须是一个停止点的事件。  
  
5.  如果应用程序正在调试生成，请发送到 SDM 的一 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 事件对象，当编码的第一个命令在运行时结构中要执行时。  此操作始终是一个停止点的事件。  当单步执行调试会话时， IDE 在此事件终止。  
  
> [!NOTE]
>  许多语言在代码的开头使用全局初始值设定项或外部，预编译函数 \(从 CRT 库或 \_Main\)。  如果要调试程序的语言包含这些类型的元素之一，在初始入口点之前，该代码运行，并且入口点事件发送，当用户入口点，例如 **主** 或 `WinMain`时，为止。  
  
## 请参阅  
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)