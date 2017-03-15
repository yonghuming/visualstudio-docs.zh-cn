---
title: "终止程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程序、 沧 ゎ ㄆ ン"
  - "调试 [调试 SDK]，终止程序"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 终止程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面是一个程序终止的声明与一个线程上。  
  
## 终止进程  
  
1.  DE 发送 [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 和有效的 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)。  
  
2.  DE 发送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 和有效的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)。  
  
 IDE 输入设计模式。  该调试引擎或运行时环境调用 [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 从端口移除程序。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)