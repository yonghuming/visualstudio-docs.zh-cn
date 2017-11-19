---
title: "启动调试器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23fd772b74c4caafbde37541933c38e306f9dc75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="launching-the-debugger"></a>启动调试器
启动调试器时，需要发送的方法和事件及其正确属性的正确的顺序。  
  
## <a name="sequences-of-methods-and-events"></a>方法和事件的序列  
  
1.  通过选择调用会话调试管理器 (SDM)**调试**菜单，，然后选择**启动**。 请参阅[启动程序](../../extensibility/debugger/launching-a-program.md)有关详细信息。  
  
2.  SDM 调用[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  
  
3.  基于调试引擎 (DE) 进程模型，`IDebugProgramNodeAttach2::OnAttach`方法返回以下方法，确定后续操作之一。  
  
     如果`S_FALSE`返回的调试引擎 (DE) 是要加载： 虚拟机。  
  
     - 或 -  
  
     如果`S_OK`则会返回，DE 是要加载的 SDM 进程内。 SDM 然后执行以下任务：  
  
    1.  调用[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)获取 DE 的引擎信息。  
  
    2.  共同创建 DE。  
  
    3.  调用[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
4.  DE 发送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)到与 SDM`EVENT_SYNC`属性。  
  
5.  DE 发送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)到与 SDM`EVENT_SYNC`属性。  
  
6.  DE 发送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)到与 SDM`EVENT_SYNC`属性。  
  
7.  DE 发送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)到与 SDM`EVENT_SYNC`属性。  
  
8.  DE 发送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)到与 SDM`EVENT_SYNC`属性。  
  
## <a name="see-also"></a>另请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)   
 [启动程序](../../extensibility/debugger/launching-a-program.md)