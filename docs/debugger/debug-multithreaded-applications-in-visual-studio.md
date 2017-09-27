---
title: "调试 Visual Studio 中的多线程应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: c5a123ccb276e01953b2168d50e0d633640d384a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>在 Visual Studio 中调试多线程应用程序
线程是操作系统向其分配处理器时间的指令序列。 在操作系统中运行的每个进程都包含至少一个线程。 包含多个线程的进程称为多线程。  
  
具有多个处理器、多核处理器或超线程进程的计算机可以同时运行多个线程。 并行处理多个线程可以极大地提高程序性能，但是，由于需要跟踪多个线程，也使得调试更加困难。  
  
此外，多线程处理会引入某些新类型的潜在 bug。 例如，通常会有两个或更多线程必须访问同一资源，但是一次只能有一个线程可以安全地访问该资源。 必须使用某种形式的互斥以确保一次仅有一个线程访问资源。 如果互斥执行不正确，它可以创建*死锁*没有线程可以在其中执行的条件。 对于调试而言，死锁是特别难解决的问题。

Visual Studio 提供用于在调试多线程应用程序中使用不同的工具。

- 对于线程，用于调试线程的主要工具是**线程**窗口中，源窗口中的线程标记**并行堆栈**窗口中，**并行监视**窗口中，和**调试位置**工具栏。 若要了解有关**线程**窗口和**调试位置**工具栏上，请参阅[演练： 使用线程窗口进行调试](../debugger/how-to-use-the-threads-window.md)。 若要了解如何使用**并行堆栈**和**并行监视**windows，请参阅[开始调试多线程应用程序](../debugger/get-started-debugging-multithreaded-apps.md)。 这两个主题演示如何使用线程标记。
  
- 使用的代码的[任务并行库 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)或[并发运行时](/cpp/parallel/concrt/concurrency-runtime/)，用于调试的主要工具是**并行堆栈**窗口中， **并行监视**窗口中，与**任务**窗口 (**任务**窗口还支持 JavaScript)。 若要开始，请参阅[演练： 调试并行应用程序](../debugger/walkthrough-debugging-a-parallel-application.md)和[演练： 调试 c + + AMP 应用程序](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)。 

- 主要工具是用于调试在 GPU 上的线程， **GPU 线程**窗口。 请参阅[如何： 使用 GPU 线程窗口](../debugger/how-to-use-the-gpu-threads-window.md)。  

- 主要工具是过程，**附加到进程**对话框中，**进程**窗口中，与**调试位置**工具栏。  
  
Visual Studio 还提供了功能强大的断点和跟踪点，在调试多线程应用程序时，它们十分有用。 可以使用断点条件和筛选器将断点置于单个线程上。 请参阅[使用断点](../debugger/using-breakpoints.md)。 
  
调试具有用户界面的多线程应用程序可能会特别困难。 在这种情况下，可以考虑在另一台机器上运行应用程序并使用远程调试。 有关信息，请参阅[远程调试](../debugger/remote-debugging.md)。  
  
## <a name="in-this-section"></a>本节内容
 [开始调试多线程应用程序](../debugger/get-started-debugging-multithreaded-apps.md)。  
 线程调试功能，主要侧重于中功能的指导的教程**并行堆栈**窗口和**并行监视**窗口。

 [用于调试线程和进程的工具](../debugger/debug-threads-and-processes.md)  
 列出用于调试线程和进程的工具的功能。  
  
 [调试多个进程](../debugger/debug-multiple-processes.md)  
 说明如何调试多个进程。

 [演练： 调试使用线程窗口](../debugger/how-to-use-the-threads-window.md)。  
 演练演示如何使用**线程**窗口和**调试位置**工具栏。 

 [演练： 调试并行应用程序](../debugger/walkthrough-debugging-a-parallel-application.md)  
 演练演示如何使用**并行堆栈**和**任务**windows。  
  
 [如何：在调试时切换到另一个线程](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 将调试上下文切换到其他线程的三种方法。  
  
 [如何：标记线程和取消标记线程](../debugger/how-to-flag-and-unflag-threads.md)  
 在调试过程中，标记要格外关注的线程，或为其设置标志。    
  
 [如何：在高性能群集上进行调试](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 对运行于高性能群集上的应用程序进行调试的技术。  

 [调试本机代码中的线程时的提示](../debugger/tips-for-debugging-threads-in-native-code.md)  
 对于调试本机线程十分有用的简单技术。 

 [如何：在本机代码中设置线程名称](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 为你的线程提供一个名称，中查看**线程**窗口。  
  
 [如何：在托管代码中设置线程名称](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 为你的线程提供一个名称，中查看**线程**窗口。 
  
## <a name="related-sections"></a>相关章节  
 [使用断点](../debugger/using-breakpoints.md)

 - 当你想要调试一个独立线程时，请使用断点条件或筛选器。  
  
 - 使用跟踪点可以在不中断的情况下跟踪程序的执行。 对于研究死锁之类的问题，这一点十分有用。  
  
 [线程处理](/dotnet/standard/threading/index)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 编程中的线程处理概念，包括代码示例。  
  
 [组件中的多线程处理](http://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 如何在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 组件中使用多线程处理。  
  
 [针对旧代码的多线程支持 (Visual C++)](/cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 针对使用 MFC 的 C++ 程序员的线程处理概念和代码示例。  
  
## <a name="see-also"></a>另请参阅  
 [调试线程和进程](../debugger/debug-threads-and-processes.md)   
 [远程调试](../debugger/remote-debugging.md)
