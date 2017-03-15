---
title: "所需的端口供应商接口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "端口供应商，所需的接口"
  - "调试 [调试 SDK]，端口供应商"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 所需的端口供应商接口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

端口提供程序必须实现 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 接口。       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 由于端口提供程序提供端口，它还必须实现它们。  因此，它必须实现以下接口:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     描述端口，并可以枚举上运行的所有进程端口。  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     提供生成，然后停止在端口处理。  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     用于运行此端口的上下文中的程序提供了一种机制注意到程序节点创建和析构。  有关更多信息，请参见 [程序节点](../../extensibility/debugger/program-nodes.md)。  
  
-   `IConnectionPointContainer`  
  
     提供 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)连接点。  
  
## 端口提供操作  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) 接收器时收到通知，当过程时，程序位于端口创建和销毁。  需要端口发送 [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) ，当过程创建和 [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) 时，处理在端口时已损坏。  还需要端口发送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ，当程序中创建并 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 时，当程序在运行于端口时的进程被销毁。  
  
 端口通常发送程序创建和销毁事件以响应 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 和 [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 方法，它们。  
  
 由于端口可能生成，然后停止物理过程和逻辑程序，必须用调试引擎还实现这些接口:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     描述物理过程。  至少必须执行下列方法:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     为 SDM 提供一种附加和分离进程。  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     描述逻辑程序。  至少必须执行下列方法:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     为 SDM 提供一种附加到此过程。  
  
## 请参阅  
 [实现端口提供程序](../../extensibility/debugger/implementing-a-port-supplier.md)