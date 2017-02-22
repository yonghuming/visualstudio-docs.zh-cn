---
title: "进程 | Microsoft Docs"
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
  - "调试 [调试 SDK]，处理"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 进程
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

根据调试器体系结构， **过程**:  
  
-   是的容器设置程序。  它类似于 windows 紧密地处理，是的容器设置线程。  
  
-   可以按名称标识自身，标识符或物理标识符。  
  
-   可以枚举所有正在运行的程序 \(及其线程\)。  
  
-   可以自我描述，它运行的端口和包含它的计算机。  
  
-   可以创建一个或多个程序，停止它创建的任何程序或导致程序停止。  
  
-   由 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 接口表示，创建，以便在进程启动时。  处理由或生成会议调试管理器 \(SDM\)或 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
 调试包可以将调试引擎 \(DE\)附加到进程通过调用 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)。  这意味着 DE 附加到运行在它可以处理的处理所有可能的过程。  例如，因此，如果公共语言运行时、附加到进程，仅附加到正在运行托管代码的程序。  
  
## 请参阅  
 [Programs](../../extensibility/debugger/programs.md)   
 [线程](../../extensibility/debugger/threads.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [调试包](../../extensibility/debugger/debug-package.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)