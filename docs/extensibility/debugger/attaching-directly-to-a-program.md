---
title: "附加到的程序直接 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8818a57d50595b3c40fa45875a1dfe23d34fb369
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="attaching-directly-to-a-program"></a>附加到的程序直接
用户想要调试程序已在通常运行的过程中按照以下步骤：  
  
1.  在 IDE 中，选择**调试进程**命令**工具**菜单。  
  
     **进程**对话框随即出现。  
  
2.  选择一个进程，然后单击**附加**按钮。  
  
     **附加到进程**对话框中，将显示列出所有的调试引擎 (DEs) 的计算机上安装。  
  
3.  指定要用于调试所选的进程，并依次 DEs**确定**。  
  
 调试包启动调试会话，并向它传递的 DEs 列表。 调试会话又将传递此列表，以及一个回调函数，为所选进程，然后向询问枚举其正在运行的程序的过程。  
  
 以编程方式，以响应用户请求，调试包实例化会话调试管理器 (SDM)，并将所选 DEs 的列表传递给它。 列表中，以及调试包将传递 SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)接口。 调试包传递到所选进程的 DEs 列表通过调用[IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)。 然后调用 SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)上要枚举进程中运行的程序的端口。  
  
 从现在开始，每种调试引擎附加到某个程序完全按照所述[附加后启动](../../extensibility/debugger/attaching-after-a-launch.md)，有两个例外。  
  
 为提高效率，实现与 SDM 共享地址空间的 DEs 进行分组，以便每个 DE 具有一组将附加到的程序。 在这种情况下， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)调用[IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)并将其传递的程序将附加到一个数组。  
  
 第二个例外情况是，发送 DE 附加到已在运行的程序的启动事件未通常包括输入点事件。  
  
## <a name="see-also"></a>另请参阅  
 [在启动之后发送启动事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)