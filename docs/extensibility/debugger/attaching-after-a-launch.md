---
title: "启动后附加 | Microsoft Docs"
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
  - "附加到程序的调试引擎"
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 启动后附加
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在程序启动后，调试会话准备将调试引擎 \(DE\)附加到前面程序。  
  
## 设计决策  
 由于通信在共享地址空间中很容易，必须确定它是否具有更多意义便于调试会话和 DE 之间的通信，或在、和程序之间。  选择在以下内:  
  
-   如果有多个有意义便于调试会话和 DE 之间的通信，则调试会话共同创建、请求和 DE 附加到程序。  这将在一个地址空间。将调试会话保留和 DE 和运行时环境和程序。在另一个。  
  
-   如果有多个有意义实现、和程序之间的通信，则运行时环境共同创建 DE。  这将在一个地址空间。将 SDM 保留和 DE、运行时环境和程序在另一个。  这是实现在解释器运行脚本语言的功能 DE。  
  
    > [!NOTE]
    >  DE 如何附加到程序是实现相关。  、和程序之间的通信也是实现相关。  
  
## 实现  
 编程，那么，当会议调试时管理器 \(SDM\)首先接收表示要生成的程序的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 对象，它调用 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) 方法，并 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 对象，稍后用于通过调试事件回到 SDM。  然后，`IDebugProgram2::Attach` 方法调用 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。  有关 SDM 方式的更多信息 `IDebugProgram2` 接收接口，请参见 [通知端口](../../extensibility/debugger/notifying-the-port.md)。  
  
 如果 DE 在地址空间需要运行与正在调试的程序，通常，因为 DE 是运行脚本的解释器的一部分， `IDebugProgramNodeAttach2::OnAttach` 方法返回 `S_FALSE`，指示已完成附加到进程。  
  
 如果为，则另一方面， DE 在 SDM 的地址空间运行， `IDebugProgramNodeAttach2::OnAttach` 方法返回 `S_OK` 或 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 接口未实现在 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 对象与正在调试的程序。  在这种情况下， [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 方法最终调用完成附加操作。  
  
 在后一种情况下，必须调用在本地程序对象传递给 `IDebugEngine2::Attach` 方法，存储 `GUID` ，并返回此 `GUID` 的 `IDebugProgram2` 对象的 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 方法时， `IDebugProgram2::GetProgramId` 方法随后调用此对象时。  `GUID` 在各种中标识程序单独调试组件。  
  
 注意对于返回 `S_FALSE`的 `IDebugProgramNodeAttach2::OnAttach` 方法， `GUID` 提供程序使用传递给该方法，它是针对本地程序对象的 `GUID` 的 `IDebugProgramNodeAttach2::OnAttach` 方法。  
  
 DE 现在附加到程序并准备发送所有启动事件。  
  
## 请参阅  
 [将直接连接到某个程序](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [通知端口](../../extensibility/debugger/notifying-the-port.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)