---
title: "将附加到程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "附加到程序的调试引擎"
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 将附加到程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在签入了正确的端口中的过程后，必须将调试器附加到要调试的程序。  
  
## 选择如何附加  
 具有会议调试管理器 \(SDM\)尝试附加到正在调试的程序的三种方式。  
  
1.  例如按调试引擎是通过 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 方法的过程 \(功能解释语言，\)， SDM 从 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 对象的 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 接口与附加的程序。  如果 SDM 可以获取 `IDebugProgramNodeAttach2` 接口，然后 SDM 调用 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。  `IDebugProgramNodeAttach2::OnAttach` 方法返回 `S_OK` 指示不附加到程序，并尝试其他可能会更改附加到程序。  
  
2.  如果 SDM 可以从附加到的程序的 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) 接口， SDM 调用 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) 方法。  此方法对由端口提供远程启动的过程很常见。  
  
3.  如果程序不能通过 `IDebugProgramNodeAttach2::OnAttach` 或 `IDebugProgramEx2::Attach` 方法附加属性， SDM 通过调用 `CoCreateInstance` 功能加载调试引擎 \(如果尚未加载\) 然后调用 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。  此方法为端口提供程序是局部程序很常见。  
  
     调用 `IDebugProgramEx2::Attach` 方法的自定义端口提供程序的实现的 `IDebugEngine2::Attach` 方法自定义端口供应商也是可能的。  通常情况下，自定义端口提供生成在远程计算机上调试引擎。  
  
 ，在会议调试管理器 \(SDM\) [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 调用方法时，附件实现。  
  
 如果运行中的 DE 同一进程中，在调试应用程序，则必须执行 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)以下方法:  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 在 `IDebugEngine2::Attach` 调用方法后，请按照 `IDebugEngine2::Attach` 方法的实现执行以下步骤:  
  
1.  发送到 SDM 的一 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 事件对象。  有关更多信息，请参见 [发送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  调用传递给 `IDebugEngine2::Attach` 方法的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 对象的 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 方法。  
  
     用于标识程序的方法返回 `GUID` 。  在表示本地程序对 DE 的对象必须存储 `GUID` ，因此，必须返回，而 `IDebugProgram2::GetProgramId` 调用方法 `IDebugProgram2` 接口时。  
  
    > [!NOTE]
    >  如果实现 `IDebugProgramNodeAttach2` 接口，程序的 `GUID` 传递给 `IDebugProgramNodeAttach2::OnAttach` 方法。  此 `GUID` 为 `IDebugProgram2::GetProgramId` 方法返回的程序的 `GUID` 使用。  
  
3.  发送一 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件对象通知 SDM 本地 `IDebugProgram2` 创建一个对象来表示程序到 DE。  有关详细信息，请参见[发送事件](../../extensibility/debugger/sending-events.md)。  
  
    > [!NOTE]
    >  这不是传递到 `IDebugEngine2::Attach` 方案的同一 `IDebugProgram2` 对象。  以前通过的 `IDebugProgram2` 对象只能由端口识别和是单独的对象。  
  
## 请参阅  
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
 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)