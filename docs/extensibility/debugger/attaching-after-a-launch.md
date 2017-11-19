---
title: "在启动后附加 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a06a9b4be6cb20339c8c89f8594f290c1f6a46a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="attaching-after-a-launch"></a>在启动后附加
已启动程序后，调试会话已准备好的调试引擎 (DE) 附加到所述的程序。  
  
## <a name="design-decisions"></a>设计决策  
 因为通信做更为简单共享的地址空间内，你必须决定是否更有意义以便于调试会话和 DE，之间或 DE 与程序之间的通信。 以下之间进行选择：  
  
-   如果它更有意义为了便于调试会话和 DE 之间的通信，调试会话并创建 DE，并询问 DE 附加到程序。 这样就使调试会话，DE 一起在一个地址空间的运行时环境和程序在另一个中同时。  
  
-   如果它更有意义便于 DE 与程序之间进行通信，运行时环境将共同创建 DE。 这将使一个地址空间中的 SDM DE、 运行时环境和程序在另一个组合在一起。 这是典型的使用解释器运行已编写脚本的语言实现 DE。  
  
    > [!NOTE]
    >  如何将 DE 附加到程序依实现而定。 DE 与程序之间的通信也是依赖于实现的。  
  
## <a name="implementation"></a>实现  
 以编程方式，当会话调试管理器 (SDM) 首先收到[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)表示要启动的程序的对象，它调用[附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)方法，将其传递[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)用于将调试事件传递回 SDM 对象，它是更高版本。 `IDebugProgram2::Attach`方法然后调用[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 有关详细信息如何 SDM 接收`IDebugProgram2`接口，请参阅[通知端口](../../extensibility/debugger/notifying-the-port.md)。  
  
 如果需要在要调试的程序，通常 DE 属于解释器运行一个脚本，因为相同的地址空间中运行你 DE`IDebugProgramNodeAttach2::OnAttach`方法返回`S_FALSE`，指示它完成附加过程。  
  
 如果 DE SDM 的地址空间中的运行另一方面，`IDebugProgramNodeAttach2::OnAttach`方法返回`S_OK`或[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)接口不所有在实现[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)与正在调试的程序关联的对象。 在这种情况下，[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法最终调用以完成附加操作。  
  
 在后一种情况，你必须调用[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法`IDebugProgram2`对象传递到`IDebugEngine2::Attach`方法时，应用商店`GUID`在本地程序对象，并返回此`GUID`时`IDebugProgram2::GetProgramId`随后对此对象调用方法。 `GUID`用于唯一地标识程序跨各种调试组件。  
  
 请注意，对于`IDebugProgramNodeAttach2::OnAttach`方法返回`S_FALSE`、`GUID`用于程序到该方法通过并且`IDebugProgramNodeAttach2::OnAttach`设置的方法`GUID`上的本地程序对象。  
  
 DE 现在被附加到程序和准备好发送任何启动事件。  
  
## <a name="see-also"></a>另请参阅  
 [附加到的程序直接](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [通知端口](../../extensibility/debugger/notifying-the-port.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)