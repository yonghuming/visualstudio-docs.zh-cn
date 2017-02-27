---
title: "DA0503：所分析的进程的平均工作集(以字节为单位) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.503"
  - "vs.performance.DA0503"
  - "vs.performance.rules.DA0503"
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0503：所分析的进程的平均工作集(以字节为单位)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0503|  
|类别|资源监控|  
|分析方法|全部|  
|消息|收集此信息的目的是仅供参考。  Process Working Set 计数器通过您分析的进程来测量物理内存使用量。  报告的值是根据所有测量时间间隔求得的平均值。|  
|规则类型|信息|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。  
  
## 规则说明  
 此消息报告进程当前使用的以字节（工作集）为单位的平均物理内存量。  进程工作集表示当前位于物理内存中的进程地址空间中的页。  
  
 报告的值包括进程已引用的共享内存段中的驻留页面。  进程引用的共享 DLL 包括在所计数的共享内存段中。  由于共享内存段的缘故，进程工作集的值可高于进程已分配的虚拟内存量。  
  
 报告的值是对所有测量时间间隔求得的平均值，在这些时间间隔中正在分析的进程处于活动状态。  
  
 此进程工作集的大小反映进程当前正在使用的虚拟内存量。  此进程工作集的大小还受可用于运行应用程序的物理内存（或 RAM）量以及其他正在运行的进程对该物理内存的争用情况所影响。  如果物理内存受约束，则进程工作集的值往往会发生很大的变化，因为操作系统会尝试通过定期修整进程工作集中完全不活动的页面在活动进程间平衡内存使用量。  
  
 有关进程工作集的更多信息，请参阅 MSDN 上 Windows 内存管理文档中的 [工作集](http://go.microsoft.com/fwlink/?LinkId=177830)。  
  
## 如何使用规则数据  
 使用此规则值可以比较程序的不同版本或内部版本的性能，或者了解不同分析方案中应用程序的性能。  
  
 双击“错误列表”窗口中的该消息以导航到分析数据的[标记视图](../profiling/marks-view.md)视图。  查找**“Process\\Working Set”**和**“Memory\\Pages\/sec”**列。  比较这两个列，并确定程序执行过程中是否有一些特定阶段看起来似乎与增加的分页 IO 活动相关联。