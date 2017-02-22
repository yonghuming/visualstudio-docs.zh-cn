---
title: "下启动程序 | Microsoft Docs"
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
  - "调试引擎启动"
  - "启动的程序"
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 下启动程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

若要调试程序的用户可以按 F5 运行从 IDE 的调试器。  这将启动最终将导致连接到调试引擎的 IDE'S，然后 \(DE\)连接的一系列事件，或附加属性，为如下过程:  
  
1.  IDE 第一次调用解决方案中的操作项目调试设置的项目包访问。  设置包括过程中运行的起始目录、环境变量、端口和 DE 对于使用创建程序，因此，如果指定。  这些设置传递到调试包。  
  
2.  如果 DE 指定， DE 调用操作系统启动程序。  作为启动程序的结果，程序的运行时环境加载。  例如，因此，如果程序在 MSIL 中，公共语言运行时将调用运行程序。  
  
     \- 或 \-  
  
     如果 DE 未指定，端口调用操作系统启动程序，导致程序的运行时环境加载。  
  
    > [!NOTE]
    >  如果、用于启动程序，可能相同的 DE 将附加到程序。  
  
3.  根据、或端口是否已启动程序，、或运行时环境中创建一个事件声明或节点，然后通知端口程序运行。  
  
    > [!NOTE]
    >  建议为运行时环境创建程序，节点，因为程序节点是可以以调试程序的轻量表示。  不需要加载整个、创建和注册程序节点。  如果 DE 旨在 IDE 过程中运行，但是， IDE 实际上未运行，需要可以添加程序节点到端口的元素。  
  
 新创建的程序，使其他所有程序时，相关或不相关，生成或附加到从同一个 IDE，构成调试会话。  
  
 编程，那么，当用户首先按 **F5**时， vsprvs 的调试包。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 方法调用与生成的程序类型\) 的项目包 \(，请解决方案中的操作项又加载一 <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> 结构调试设置。  此结构传回调试包通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> 方法。  调试包然后实例化该会话调试管理器 \(SDM\)，是正在调试的程序，并关联的任何调试引擎。  
  
 之一传递给 SDM 是要使用的 DE 的 GUID 启动程序。  
  
 如果 DE GUID 不是 `GUID_NULL`， SDM 共同创建、，然后调用其 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 方法启动程序。  例如，因此，如果程序是用本机代码编写，然后 `IDebugEngineLaunch2::LaunchSuspended` 可能会调用 `CreateProcess` 和 `ResumeThread` \(Win32 函数\) 运行程序。  
  
 作为启动程序的结果，程序的运行时环境加载。  DE 或运行时环境中创建一 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 接口描述程序并通过此接口来 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 通知端口程序运行。  
  
 如果 `GUID_NULL` 通过，则端口启动程序。  在程序运行时，运行时环境创建一 `IDebugProgramNode2` 接口描述程序并将其传递给 `IDebugPortNotify2::AddProgramNode`。  会通知端口程序运行。  然后 SDM 将调试引擎附加到正在运行的程序。  
  
## 本节内容  
 [通知端口](../../extensibility/debugger/notifying-the-port.md)  
 解释发生的情况，在程序启动后，并且端口收到通知。  
  
 [启动后附加](../../extensibility/debugger/attaching-after-a-launch.md)  
 ，在调试会话准备附加 DE 到过程，文档。  
  
## 相关章节  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向各种调试任务，如启动程序并计算表达式。