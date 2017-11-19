---
title: "附加和分离到某个程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71f678852b4d16d0b7c6f150abae03c6c4cdcad4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="attaching-and-detaching-to-a-program"></a>附加和分离到程序
附加调试器需要发送的方法和具有正确的属性的事件正确的顺序。  
  
## <a name="sequence-of-methods-and-events"></a>方法和事件的序列  
  
1.  会话调试管理器 (SDM) 调用[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  
  
     基于调试引擎 (DE) 进程模型，`IDebugProgramNodeAttach2::OnAttach`方法返回以下方法，确定后续操作之一。  
  
     如果`S_FALSE`的调试引擎已成功附加到程序的返回。 否则为[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法调用以完成附加过程。  
  
     如果`S_OK`返回，DE 将是在与 SDM 相同的进程中加载。 SDM 执行以下任务：  
  
    1.  调用[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)获取 DE 的引擎信息。  
  
    2.  共同创建 DE。  
  
    3.  调用[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
2.  DE 发送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)到与 SDM`EVENT_SYNC`属性。  
  
3.  DE 发送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)到与 SDM`EVENT_SYNC`属性。  
  
4.  DE 发送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)到与 SDM`EVENT_SYNC_STOP`属性。  
  
 从程序分离是一个简单、 两步过程，如下所示：  
  
1.  SDM 调用[分离](../../extensibility/debugger/reference/idebugprogram2-detach.md)。  
  
2.  DE 发送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。  
  
## <a name="see-also"></a>另请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)