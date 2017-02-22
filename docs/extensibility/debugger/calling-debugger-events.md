---
title: "调用调试器事件 | Microsoft Docs"
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
  - "调试 [调试 SDK] 事件"
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 调用调试器事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

事件在调试会话中按特定顺序发生。  
  
## 讨论  
 若要了解模式对调试引擎 \(DE\)和会话之间调试管理器 \(SDM\)，以下表示在典型的调试会话中发生的事件的调用的顺序:  
  
1.  [附加和分离到程序](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [启动调试器](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [停止程序](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [创建断点](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [当断点绑定或变为断开连接](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [断点错误](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [命中断点](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [删除断点](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [进入中断模式](../../extensibility/debugger/entering-break-mode.md)  
  
10. [单步执行中断模式](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [表达式计算在中断模式](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [异常处理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## 请参阅  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)