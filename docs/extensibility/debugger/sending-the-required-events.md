---
title: "发送所需的事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30a5b1150d44c138465db36da2b032b71f075397
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sending-the-required-events"></a>发送所需的事件
用于发送所需的事件使用此过程。  
  
## <a name="process-for-sending-required-events"></a>用于发送所需的事件的过程  
 以下事件是必需的此顺序时创建调试引擎 (DE), 和附加到的程序中：  
  
1.  发送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)到会话调试管理器 (SDM) DE 初始化用于调试的进程中的一个或多个程序时的事件对象。  
  
2.  要调试程序附加到，请发送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)到 SDM 事件对象。 此事件可能 stopping 事件，具体取决于你引擎的设计。  
  
3.  如果程序附加到进程启动时，发送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)到 SDM 以通知新线程的 IDE 的事件对象。 此事件可能 stopping 事件，具体取决于你引擎的设计。  
  
4.  发送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)到 SDM 被调试的程序时完成的加载或完成时，将附加到的程序的事件对象。 此事件必须停止事件。  
  
5.  如果启动要调试应用程序时，发送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)到 SDM 将要执行的运行时体系结构中的代码的第一个指令时的事件对象。 此事件始终是停止事件。 当单步执行到调试会话，IDE 将停止对此事件。  
  
> [!NOTE]
>  许多语言使用他们的代码开头的全局初始值设定项或外部的预编译的函数 （从的 CRT 库或 _Main）。 如果在调试程序的语言包含以下任一这些类型的元素之前的初始入口点，然后运行此代码并不会发送入口点事件的用户入口点时，如**主要**或`WinMain`，为止。  
  
## <a name="see-also"></a>另请参阅  
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)