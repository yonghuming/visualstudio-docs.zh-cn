---
title: "DA0017：以分页方式将活动内存移到磁盘的发生率高 | Microsoft Docs"
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
  - "vs.performance.17"
  - "vs.performance.rules.DA0017"
  - "vs.performance.DA0017"
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0017：以分页方式将活动内存移到磁盘的发生率高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0017|  
|类别|内存和分页|  
|分析方法|全部|  
|消息|以分页方式将活动内存移到磁盘的发生率高。  您的应用程序可能受内存限制。|  
|规则类型|信息|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。  
  
## 原因  
 在分析运行中收集的系统性能数据表明，在整个分析运行期间以分页方式将活动内存移到磁盘以及从磁盘移动活动内存的发生率高。  此级别的分页率通常会影响应用程序的性能和响应速度。  请考虑通过修改算法来减少内存分配。  此外，还可能需考虑应用程序的内存要求。  
  
## 规则说明  
  
> [!NOTE]
>  当活动内存的分页级别达到相当大的数目时，将激发此信息规则。  如果发生过高级别的分页，则将改为激发警告规则 [DA0014：以分页方式将活动内存移到磁盘的发生率极高](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)。  
  
 以分页方式向磁盘移动内存过频可能是由于物理内存不足导致的。  如果分页操作决定分页文件所在物理磁盘的使用，那么，这些操作可能会使对同一磁盘的其他面向应用程序的磁盘操作的速度变慢。  
  
 通常通过批量分页操作从磁盘读取页面或将页面写入磁盘。  举例来说，Pages Output\/sec 的数值通常比 Page Writes\/sec 的数值大很多。  这是由于 Pages Output\/sec 还包括系统文件缓存中的已更改数据页面。  但是，有时候难以确定哪个进程直接负责分页或者为什么是这个进程。  
  
## 如何解决冲突  
 双击“错误列表”窗口中的该消息以导航到[标记](../profiling/marks-view.md)视图。  查找**“Memory\\Pages\/sec”**列。  确定程序执行过程中是否有一些特定阶段的分页 IO 活动多于其他阶段。  
  
 如果要收集负载测试方案中 ASP.NET 应用程序的分析数据，请尝试在配置了额外物理内存（或 RAM）的计算机上重新运行负载测试。  
  
 请考虑通过修改算法和避免使用非常占用内存的 API（如 String.Concat 和 String.Substring）来减少内存分配。