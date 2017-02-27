---
title: "调试器概念 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]"
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 调试器概念
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

若要在 Visual Studio 调试包，需要熟悉用于设计包的体系结构概念。  
  
## 本节内容  
 [调试会话](../../extensibility/debugger/debug-session.md)  
 解释会话的效果在调试结构中。  
  
 [服务器](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 定义哪些服务器是基于调试体系结构，通过概要论述和实际术语。  
  
 [端口供应商](../../extensibility/debugger/port-suppliers.md)  
 定义了端口提供程序是基于调试体系结构。  
  
 [端口](../../extensibility/debugger/ports.md)  
 定义了端口是基于调试体系结构。  
  
 [进程](../../extensibility/debugger/processes.md)  
 定义了处理是基于调试体系结构。  
  
 [程序节点](../../extensibility/debugger/program-nodes.md)  
 定义过程节点基于调试体系结构，包括它如何能够确定自身及其运行的进程。  
  
 [Programs](../../extensibility/debugger/programs.md)  
 定义一个程序根据调试体系结构。  
  
 [线程](../../extensibility/debugger/threads.md)  
 定义线程的属性根据调试体系结构。  
  
 [堆栈帧](../../extensibility/debugger/stack-frames.md)  
 定义一个堆栈帧基于调试体系结构。  堆栈帧是提供线程的执行上下文堆栈的抽象。  
  
 [模块](../../extensibility/debugger/modules.md)  
 定义一个模块，具体取决于调试体系结构，作为物理容器代码，如可执行文件或 DLL。  
  
 [断点](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 定义断点挂起状态，区域的三个类型和错误在调试体系结构的术语。  
  
## 相关章节  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)  
 解释调试引擎 \(DE\)如何在代码、文档和表达式计算上下文中同时运行。  支持三种上下文、位置、位置或计算都描述，与之相关。  
  
 [调试程序组件](../../extensibility/debugger/debugger-components.md)  
 提供调试组件的 Visual Studio 概述，包括调试引擎 \(DE\)、表达式计算器 \(EE\)和符号处理程序 \(SH\)。  
  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向各种调试任务，如启动程序并计算表达式。