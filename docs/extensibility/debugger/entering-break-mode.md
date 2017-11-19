---
title: "进入中断模式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33dd97cf627ae10e71a2aa2213a9763e86818b70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="entering-break-mode"></a>进入中断模式
以下描述当在单步执行、 运行到的源代码中，有光标的行或运行到断点后遇到断点时出现的过程。  
  
## <a name="break-mode-process"></a>中断模式下进程  
  
1.  调试引擎 (DE) 将发送[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)， [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)，或任何其他停止事件以使 IDE 进入中断模式。  
  
2.  SDM，如下所示获取从线程的调用堆栈信息：  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)若要获取源代码信息  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)若要获取的文件名称  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)以获得语句范围  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)获取内存信息  
  
## <a name="see-also"></a>另请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)