---
title: "DA0039：锁争用率非常高 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.39"
  - "vs.performance.DA0039"
  - "vs.performance.rules.DA0039"
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0039：锁争用率非常高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0039|  
|类别|.NET Framework 使用|  
|分析方法|采样<br /><br /> 检测<br /><br /> .NET 内存|  
|消息|.NET 锁争用的发生率非常高。  请运行并发分析，以调查此锁争用的原因。|  
|规则类型|警告|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 25 个样本才能触发此规则。  
  
## 原因  
 随分析数据一起收集的系统性能数据表明，应用程序执行期间锁争用的发生率过高。  请考虑使用并发分析方法重新进行分析，以找出争用的原因。  
  
## 规则说明  
 锁用于保护代码的关键段，这些段在多线程应用程序中一次只能由一个线程按顺序执行。  Microsoft .NET 公共语言运行时 \(CLR\) 提供一整套同步基元和锁定基元。  举例来说，C\# 语言支持 lock 语句（在 Visual Basic 中为 SyncLock）。  托管应用程序可以调用 System.Threading 命名空间中的 Monitor.Enter 和 Monitor.Exit 方法，以直接获取和释放锁。  .NET Framework 支持额外的同步基元和锁定基元，其中包括支持 Mutexes、ReaderWriterLocks 和 Semaphores 的类。  有关更多信息，请参见 MSDN 网站上.NET Framework 开发人员指南中的同步基元[概述](http://go.microsoft.com/fwlink/?LinkId=177867)。  这些 .NET Framework 类本身位于 Windows 操作系统内置的较低级别同步服务之上。  它们包括关键代码段对象和许多不同的 Wait 和事件信号发送函数。  有关更多信息，请参见 MSDN Library 中Win32的 [同步](http://go.microsoft.com/fwlink/?LinkId=177869) 部分和 COM 开发。  
  
 在用于同步和锁定的 .NET Framework 类和 Windows 本机对象下面，是必须使用互锁操作更改的共享内存位置。  互锁操作使用特定于硬件的指令，这些指令通过原子操作处理共享内存位置以更改其状态。  原子操作在计算机中的所有处理器之间一定是一致的。  Locks 和 WaitHandles 是在被设置或重置时自动使用互锁操作的 .NET 对象。  应用程序中可能会有其他共享内存数据结构同样要求使用互锁操作，以便采用线程安全方式进行更新。  有关更多信息，请参见 MSND Library 的 .NET Framework 部分的 [互锁操作](http://go.microsoft.com/fwlink/?LinkId=177870)  
  
 同步和锁定是用于确保多线程应用程序正确执行的机制。  多线程应用程序的每个线程都是独立的执行单元，由操作系统独立进行安排。  每当一个尝试获取锁的线程由于另一个线程占用该锁而被延迟时，就会发生锁争用。  
  
 锁经常嵌套在一起。  当执行关键代码段的线程执行随后需要另一个锁的函数时，就会发生嵌套。  些许锁嵌套是无法避免的。  关键代码段可能会调用一个依靠锁来确保线程安全性的 .NET Framework 方法。  如果从应用程序中的某个关键代码段调入 Framework 方法，该方法用不同锁句柄也进行了锁定，则会导致锁嵌套。  嵌套锁定情况可能会导致公认的难以解决和修复的性能问题。  
  
 如果分析运行期间执行的测量表明存在过量锁争用情况，则会激发此规则。  锁争用将延迟执行等待锁的线程。  低端硬件上运行的单元测试或负载测试中即使出现相当少量的锁争用，也应进行调查。  
  
> [!NOTE]
>  当分析数据中报告的锁争用的发生率非常高但未过量时，将激发 [DA0038：锁争用率很高](../profiling/da0038-high-rate-of-lock-contentions.md)信息消息，而不是此警告消息。  
  
## 如何调查警告  
 双击该消息以导航到分析数据的[标记](../profiling/marks-view.md)视图。找到**“.NET CLR LocksAndThreads\\Contention Rate \/ sec”**列。  确定程序执行过程中是否有一些特定阶段的锁争用情况多于其他阶段。  
  
 仅当未使用并发分析方法时，才会激发此规则。  并发分析方法是用于诊断应用程序中与锁争用相关的性能问题的最佳工具。  收集并发分析数据以了解应用程序的锁定行为。  这包括了解哪些锁的争用很激烈、等待争用锁的线程要延迟多久才能执行，以及其中牵涉了哪些特定代码。  并发分析收集所有锁争用的相关数据，其中包括本机 Windows 功能的锁定行为、.NET Framework 类以及您的应用程序引用的任何其他第三方库。  有关 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中的并发分析的信息，请参见[收集线程和进程并发数据](../profiling/collecting-thread-and-process-concurrency-data.md)。  有关指向命令行中并发分析相关信息的链接，请参见[从命令行使用分析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)的**Using the Concurrency Method to Collect Resource Contention and Thread Activity Data**一节。