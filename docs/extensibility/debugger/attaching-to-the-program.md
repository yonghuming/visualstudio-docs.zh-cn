---
title: "附加到的程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7dd4baed877bd5d0262e966edf006dea80596b47
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="attaching-to-the-program"></a>附加到程序
你向适当的端口注册您的程序后，你必须将调试器附加到你想要调试的程序。  
  
## <a name="choosing-how-to-attach"></a>选择如何将附加  
 有三种方法会话调试管理器 (SDM) 尝试附加到正在调试的程序。  
  
1.  程序的调试引擎通过启动[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法 （典型的解释语言，例如），SDM 获取[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)从接口[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)与附加到程序关联的对象。 如果可以获得 SDM`IDebugProgramNodeAttach2`接口，然后调用 SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 `IDebugProgramNodeAttach2::OnAttach`方法返回`S_OK`以指示它未附加到程序和可以进行其他尝试附加到程序。  
  
2.  如果可以获得 SDM [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)接口从附加到 SDM 调用程序[附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)方法。 这种方法是典型的端口提供程序由远程启动的程序。  
  
3.  如果程序不能通过附加`IDebugProgramNodeAttach2::OnAttach`或`IDebugProgramEx2::Attach`方法，SDM 加载 （如果尚未加载） 的调试引擎通过调用`CoCreateInstance`函数，然后调用[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。 这种方法是程序启动本地端口供应商的典型方式。  
  
     你也可用于自定义端口的供应商联系，以调用`IDebugEngine2::Attach`方法的自定义端口供应商的实现中`IDebugProgramEx2::Attach`方法。 通常在这种情况下，自定义端口提供程序将启动远程计算机上的调试引擎。  
  
 当会话调试管理器 (SDM) 调用实现附件[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
 如果在与要调试应用程序相同的进程中运行你 DE，则必须实现以下的方法[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)，  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 后`IDebugEngine2::Attach`调用方法，请按照这些步骤的实现中`IDebugEngine2::Attach`方法：  
  
1.  发送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)到 SDM 事件对象。 有关详细信息，请参阅[发送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  调用[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)对象传递到`IDebugEngine2::Attach`方法。  
  
     这将返回`GUID`用于找出的程序。 `GUID`必须存储在对象，表示本地编程为 DE，且必须返回时`IDebugProgram2::GetProgramId`方法调用`IDebugProgram2`接口。  
  
    > [!NOTE]
    >  如果你实现`IDebugProgramNodeAttach2`接口，该程序的`GUID`传递给`IDebugProgramNodeAttach2::OnAttach`方法。 这`GUID`用于程序的`GUID`返回`IDebugProgram2::GetProgramId`方法。  
  
3.  发送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件对象，以通知 SDM，本地`IDebugProgram2`创建对象来表示 DE 到的程序。 有关详细信息，请参阅[发送事件](../../extensibility/debugger/sending-events.md)。  
  
    > [!NOTE]
    >  这是不相同`IDebugProgram2`对象已传递到`IDebugEngine2::Attach`方法。 以前传递`IDebugProgram2`对象端口仅被识别，并为一个单独的对象。  
  
## <a name="see-also"></a>另请参阅  
 [启动基于附件](../../extensibility/debugger/launch-based-attachment.md)   
 [发送事件](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)