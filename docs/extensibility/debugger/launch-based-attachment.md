---
title: "启动基于附件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎启动"
  - "附加到程序的调试引擎"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 启动基于附件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以编程的基于生成的附件是自动的。  当承载程序的进程由 SDM 时生成，基于生成的附件的路径类似于手动附件方法。  有关信息，请参见 [附加到程序](../../extensibility/debugger/attaching-to-the-program.md)。  
  
## 附加的进程  
 主要区别是遵循 **附加** 的事件序列调用，如下所示:  
  
1.  发送到 SDM 的一 **IDebugEngineCreateEvent2** 事件对象。  有关详细信息，请参见 [发送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  调用 **IDebugProgram2** 接口的 `IDebugProgram2::GetProgramId` 方法将传递给 **附加** 方法。  
  
3.  发送一 **IDebugProgramCreateEvent2** 事件对象通知 SDM 本地 **IDebugProgram2** 创建一个对象来表示程序到 DE。  
  
4.  发送一 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 事件对象通知 SDM 新线程对生成的进程中创建。  
  
## 请参阅  
 [发送所需的事件](../../extensibility/debugger/sending-the-required-events.md)   
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)