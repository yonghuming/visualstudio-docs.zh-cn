---
title: "进入中断模式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中断模式"
  - "调试 [调试 SDK]，进入中断模式"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 进入中断模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述发生的处理，以在断点逐句遇到时向功能后，运行到源代码行具有光标位于它，或者运行到断点。  
  
## 中断模式的进程  
  
1.  调试引擎 \(DE\)发送 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)、 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)，或其他终止的事件会导致 IDE 进入中断模式。  
  
2.  SDM 从线程获取调用堆栈信息，如下所示:  
  
    -   [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2:: GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)  
  
    -   [IEnumDebugFrameInfo2:: 接下来](../Topic/IEnumDebugFrameInfo2::Next.md)  
  
    -   [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 获取源代码信息  
  
    -   [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) 获取文件名  
  
    -   [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) get 语句范围  
  
    -   [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) 访问内存信息  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)