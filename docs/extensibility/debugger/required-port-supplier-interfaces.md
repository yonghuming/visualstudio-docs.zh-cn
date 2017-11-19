---
title: "所需端口供应商接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 973d191305383967aee1c7379fd203375a71c825
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="required-port-supplier-interfaces"></a>所需的端口供应商接口
端口提供程序必须实现[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)接口。[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 由于端口供应商提供的端口，则它还必须实现它们。 因此，它必须实现以下接口：  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     介绍端口，并可以枚举运行在端口上的所有进程。  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     提供启动和终止的端口上的进程。  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     提供用于在此端口上下文进行通知的程序节点创建和析构中运行的程序的机制。 有关详细信息，请参阅[程序节点](../../extensibility/debugger/program-nodes.md)。  
  
-   `IConnectionPointContainer`  
  
     提供的连接点[IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)。  
  
## <a name="port-supplier-operation"></a>端口供应商操作  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)接收器接收当进程时发送通知和程序创建和销毁上一个端口。 将发送所需的端口[IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md)时创建一个进程和[IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)进程在端口上被销毁时。 端口也需要发送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)时创建的程序和[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)程序在端口上运行的进程中被销毁时。  
  
 端口通常发送程序创建和销毁事件以响应[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)和[RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)方法，分别。  
  
 因为一个端口可以启动和终止进程物理和逻辑的程序，还必须通过的调试引擎中实现这些接口：  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     描述物理过程。 至少必须实现以下方法：  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     提供 SDM 附加和分离本身从进程的方法。  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     描述逻辑的程序。 至少必须实现以下方法：  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     提供 SDM 附加到此程序的方法。  
  
## <a name="see-also"></a>另请参阅  
 [实现端口提供程序](../../extensibility/debugger/implementing-a-port-supplier.md)