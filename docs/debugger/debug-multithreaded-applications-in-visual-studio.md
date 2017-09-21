---
title: "在 Visual Studio 中调试多线程应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试 [Visual Studio], 高性能计算"
  - "调试 [Visual Studio], 多线程"
  - "高性能调试"
  - "多线程调试"
  - "线程处理 [Visual Studio], 调试"
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在 Visual Studio 中调试多线程应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

线程是操作系统向其分配处理器时间的指令序列。  在操作系统中运行的每个进程都包含至少一个线程。  包含多个线程的进程称为多线程。  
  
 具有多个处理器、多核处理器或超线程进程的计算机可以同时运行多个线程。  并行处理多个线程可以极大地提高程序性能，但是，由于需要跟踪多个线程，也使得调试更加困难。  
  
 此外，多线程处理会引入某些新类型的潜在 bug。  例如，通常会有两个或更多线程必须访问同一资源，但是一次只能有一个线程可以安全地访问该资源。  必须使用某种形式的互斥以确保一次仅有一个线程访问资源。  如果互斥执行不正确，则可能形成死锁条件，这种条件下，任何线程都无法执行。  对于调试而言，死锁是特别难解决的问题。  
  
 Visual Studio 提供了**“线程”**窗口、“GPU 线程”窗口、“并行监视”窗口和其他可简化多线程调试的功能。 了解线程界面功能的最佳方法是执行演练。  请参阅[演练：调试多线程应用程序](../debugger/walkthrough-debugging-a-multithreaded-application.md)和[演练：调试 C\+\+ AMP 应用程序](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)。  
  
 Visual Studio 还提供了功能强大的断点和跟踪点，在调试多线程应用程序时，它们十分有用。  可以使用断点筛选器将断点置于单个线程上。  请参阅[使用断点](../debugger/using-breakpoints.md)  
  
 调试具有用户界面的多线程应用程序可能会特别困难。  在这种情况下，可以考虑在另一台机器上运行应用程序并使用远程调试。  有关详细信息，请参阅[远程调试](../debugger/remote-debugging.md)。  
  
## 本节内容  
 [调试线程和进程](../debugger/debug-threads-and-processes.md)  
 说明调试线程和进程的基础知识。  
  
 [调试进程](../debugger/debug-multiple-processes.md)  
 说明如何调试多个进程。  
  
 [如何：使用“线程”窗口](../debugger/how-to-use-the-threads-window.md)  
 通过**“线程”**窗口调试线程的实用过程。  
  
 [如何：在调试时切换到另一个线程](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 将调试上下文切换到其他线程的三种方法。  
  
 [如何：标记线程和取消标记线程](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md)  
 在调试过程中，标记要格外关注的线程，或为其设置标志。  
  
 [如何：在本机代码中设置线程名称](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 为在**“线程”**窗口中查看的线程提供一个名称。  
  
 [如何：在托管代码中设置线程名称](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 为在**“线程”**窗口中查看的线程提供一个名称。  
  
 [演练：调试多线程应用程序](../debugger/walkthrough-debugging-a-multithreaded-application.md)。  
 一部关于线程调试功能的指导教程，重点介绍如何使用 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 的功能。  
  
 [如何：在高性能群集上进行调试](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 对运行于高性能群集上的应用程序进行调试的技术。  
  
 [调试本机代码中的线程时的提示](../debugger/tips-for-debugging-threads-in-native-code.md)  
 对于调试本机线程十分有用的简单技术。  
  
 [使用“任务”窗口](../debugger/using-the-tasks-window.md)  
 显示所有托管或本机任务对象（包括其状态和其他有用信息）的列表。  
  
 [使用“并行堆栈”窗口](../debugger/using-the-parallel-stacks-window.md)  
 在单个视图中显示多个线程（或任务）的调用堆栈，并且还将合并这些线程（或任务）公共的堆栈段。  
  
 [演练：调试并行应用程序](../debugger/walkthrough-debugging-a-parallel-application.md)  
 演练演示如何使用“并行任务”和“并行堆栈”窗口。  
  
 [如何：使用“并行监视”窗口](../debugger/how-to-use-the-parallel-watch-window.md)  
 检查多个线程中的值和表达式。  
  
 [如何：使用“GPU 线程”窗口](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
 检查并使用调试过程中在 GPU 上运行的线程。  
  
## 相关章节  
 [使用断点](../debugger/using-breakpoints.md)  
 -   如果要将一个断点置于单个线程上，可以使用断点筛选器。  
  
-   使用跟踪点可以在不中断的情况下跟踪程序的执行。  对于研究死锁之类的问题，这一点十分有用。  
  
 [Threading](../Topic/Managed%20Threading.md)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 编程中的线程处理概念，包括代码示例。  
  
 [组件中的多线程处理](../Topic/Multithreading%20in%20Components.md)  
 如何在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 组件中使用多线程处理。  
  
 [针对旧代码的多线程支持 \(Visual C\+\+\)](/visual-cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 针对使用 MFC 的 C\+\+ 程序员的线程处理概念和代码示例。  
  
## 请参阅  
 [调试线程和进程](../debugger/debug-threads-and-processes.md)   
 [远程调试](../debugger/remote-debugging.md)