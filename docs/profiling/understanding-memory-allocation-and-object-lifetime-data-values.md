---
title: "了解分析工具中的内存分配数据值和对象生存期数据值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 内存分析方法"
  - "分析工具，.NET 内存方法"
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 了解分析工具中的内存分配数据值和对象生存期数据值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当事件发生的附加信息时，该*.NET内存分配*[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]分析工具收集有关分配被创建或销毁的垃圾收集的对象的大小和数量的信息和分析方法有关函数*call栈*。  调用堆栈是一个动态结构，用于存储有关正在处理器上执行的函数的信息。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 该内存分析器中断计算机处理器用在一个分析的应用程序的.NET Framework对象的每个分配。  同时收集对象生存期数据时，探查器会在每次 .NET Framework 垃圾回收后中断处理器。  系统将集中每个被分析函数和每种类型对象的数据。  
  
## 分配数据  
 发生 .Net 内存事件时，将累加所分配或所销毁的内存对象的总数和大小。  
  
 发生 .Net 内存分配事件时，探查器将累加调用堆栈上每个函数的样本数。  收集数据后，调用堆栈上当前只有一个函数正在执行其函数体内的代码。  堆栈上的其他函数是函数调用层次结构中的父级，正在等待其调用的函数返回。  
  
-   对于分配事件，探查器将累加当前执行其指令的函数的独占样本数。  由于独占样本也是函数的总（非独占）样本的一部分，因此还将累加当前活动函数的非独占样本数。  
  
-   探查器递增调用堆栈上所有其他函数的非独占样本计数。  
  
## 生存期数据  
 .NET Framework 的垃圾回收器负责管理应用程序的内存分配和释放。  为优化垃圾回收器的性能，将托管堆分为三代：第 0 代、第 1 代和第 2 代。  运行时的垃圾回收器将新对象存储在第 0 代中。  未回收的对象会被提升并存储在第 1 代和第 2 代中。  
  
 垃圾回收器通过解除对整代对象的分配来回收内存。  对于被分析应用程序所创建的对象，“对象生存期”视图显示对象的数量和大小，以及回收对象时属于哪一代。