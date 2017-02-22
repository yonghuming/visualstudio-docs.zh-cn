---
title: "DA0021: 第 1 代垃圾回收的速率很高 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.21"
  - "vs.performance.DA0021"
  - "vs.performance.rules.DA0021"
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0021: 第 1 代垃圾回收的速率很高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0021|  
|类别|.NET Framework 使用|  
|分析方法|全部|  
|消息|第 1 代垃圾回收的发生率非常高。  如果特意分配程序的大多数数据结构并将其保留很长一段时间，这通常不会成为问题。  但是，如果此行为是无意的，则可能是您的应用程序锁定了对象。  如果不确定，可以收集 .NET 内存分配数据和对象生存期信息，以了解应用程序使用的内存分配模式。|  
|规则类型|信息|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。  
  
## 原因  
 分析期间收集的系统性能数据表明，与第 0 代数据收集相比，第 1 代垃圾回收中回收了 .NET Framework 对象的很大一部分内存。  
  
## 规则说明  
 Microsoft .NET 公共语言运行时 \(CLR\) 提供了自动内存管理机制，该系统使用垃圾回收器从应用程序不再使用的对象回收内存。  垃圾回收器是面向代的，并假定许多分配的生存期都较短。  例如，本地变量的生存期应比较短。  新创建的对象从第 0 代 \(gen 0\) 开始，然后如果这些对象在运行垃圾回收后仍然存在，则它们进入第 1 代，最后如果应用程序仍然使用这些对象，则它们最终进入第 2 代。  
  
 第 0 代的对象常被收集而且通常收集效率非常高。  第 1 代的对象收集得较少而且收集效率较低。  最后，应更少地收集第 2 代生存期长的对象。  第 2 代回收运行的是完整垃圾回收，也是最消耗资源的操作。  
  
 如果发生第 1 代垃圾回收的发生率过高，则会激发此规则。  如果在第 0 代回收后仍然存在太多生存期较短的对象，但随后可以在第 1 代回收中回收这些对象，则内存管理的成本可能会变得过高。  有关更多信息，请参见MSDN网站上发布在Rico Mariani's Performance Tidbits的 [中年危机](http://go.microsoft.com/fwlink/?LinkId=177835) 。  
  
## 如何调查警告  
 双击“错误列表”窗口中的该消息以导航到分析数据的[“标记”视图](../profiling/marks-view.md)。  找到**“.NET CLR Memory\\\# of Gen 0 Collections”**和**“.NET CLR Memory\\\# of Gen 1 Collections”**列。  确定程序执行过程中是否有一些特定阶段的垃圾回收较为频繁。  将这些值与**“% Time in GC”**列进行比较，看托管内存分配模式是否是导致内存管理开销过大的原因。  
  
 若要了解应用程序的托管内存使用模式，可通过运行 .NET 内存分配分析对其重新进行分析，并请求对象生存期测量。  
  
 有关如何提高垃圾回收性能的信息，请参见 Microsoft 网站上的 [垃圾回收器基础知识和性能提示](http://go.microsoft.com/fwlink/?LinkId=148226)。  有关自动垃圾回收的开销信息，请参见 [大型对象堆揭密](http://go.microsoft.com/fwlink/?LinkId=177836)。