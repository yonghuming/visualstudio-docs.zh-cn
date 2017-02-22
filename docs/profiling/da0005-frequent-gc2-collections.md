---
title: "DA0005：频繁进行 GC2 收集 | Microsoft Docs"
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
  - "vs.performance.DA0005"
  - "vs.performance.rules.DAManyGC2Collections"
  - "vs.performance.5"
  - "vs.performance.rules.DA0005"
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0005：频繁进行 GC2 收集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0005|  
|类别|.NET Framework 使用|  
|分析方法|.NET 内存|  
|消息|您的很多对象都是通过第 2 代垃圾回收来收集的。|  
|消息类型|警告|  
  
## 原因  
 在第 2 代垃圾回收中正在回收大量 .NET 内存对象。  
  
## 规则说明  
 Microsoft .NET 公共语言运行时 \(CLR\) 提供了自动内存管理机制，该系统使用垃圾回收器从应用程序不再使用的对象回收内存。  垃圾回收器是面向代的，并假定许多分配的生存期都较短。  例如，本地变量的生存期应比较短。  新创建的对象从第 0 代 \(gen 0\) 开始，然后如果这些对象在运行垃圾回收后仍然存在，则它们进入第 1 代，最后如果应用程序仍然使用这些对象，则它们最终进入第 2 代。  
  
 第 0 代的对象常被收集而且通常收集效率非常高。  第 1 代的对象收集得较少而且收集效率较低。  最后，应更少地收集第 2 代生存期长的对象。  第 2 代回收运行的是完整垃圾回收，也是最消耗资源的操作。  
  
 如果发生第 2 代垃圾回收的发生率过高，则会激发此规则。  如果在第 1 代回收后仍然存在太多生存期相对较短的对象，但随后可以在第 2 代完整回收中进行回收，则内存管理的成本可能很容易会变得过高。  For more information, see the [Mid\-life crisis](http://go.microsoft.com/fwlink/?LinkId=177835) post on the Rico Mariani's Performance Tidbits on the MSDN Web site.  
  
## 如何调查警告  
 请查看[.NET 内存数据视图](../profiling/dotnet-memory-data-views.md)报告以了解应用程序的内存分配模式。  使用[“对象生存期”视图](../profiling/object-lifetime-view.md)确定存在于第 2 代中，然后从此代被回收的程序数据对象。  使用 [“分配”视图](../profiling/dotnet-memory-allocations-view.md)确定导致这些分配的执行路径。  
  
 有关如何提高垃圾回收性能的信息，请参见 Microsoft 网站上的 [垃圾回收器基础知识和性能提示](http://go.microsoft.com/fwlink/?LinkId=148226)。  有关自动垃圾回收的开销信息，请参见 [大型对象堆揭密](http://go.microsoft.com/fwlink/?LinkId=177836)。