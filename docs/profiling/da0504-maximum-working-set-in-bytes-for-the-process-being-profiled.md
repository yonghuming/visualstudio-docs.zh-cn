---
title: "DA0504：所分析的进程的最大工作集(以字节为单位) | Microsoft Docs"
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
  - "vs.performance.DA0504"
  - "vs.performance.504"
  - "vs.performance.rules.DA0504"
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0504：所分析的进程的最大工作集(以字节为单位)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0504|  
|类别|资源管理|  
|分析方法|全部|  
|消息|收集此信息的目的是仅供参考。  Process Working Set 计数器通过您分析的进程来测量物理内存使用量。  报告的值是在所有测量时间间隔上观察到的最大值。|  
|规则类型|信息|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。  
  
## 规则说明  
 此消息报告进程当前使用的以字节为单位的最大物理内存。  进程工作集表示当前位于物理内存中的进程地址空间中的页。  此规则报告分析处于活动状态时进程工作集的最大值。  
  
 报告的值包括进程已引用的共享内存段中的驻留页面。  进程引用的共享 DLL 包括在所计数的共享内存段中。  由于共享内存段的缘故，进程工作集的值可高于进程已分配的虚拟内存量。  
  
 此进程工作集的大小反映进程当前正在使用的虚拟内存量。  此进程工作集的大小还受可用于运行应用程序的物理内存（或 RAM）量以及其他正在运行的进程对该物理内存的争用情况所影响。  有关进程工作集的更多信息，请参阅 MSDN 上 Windows 内存管理文档中的 [工作集](http://go.microsoft.com/fwlink/?LinkId=177830)。  
  
## 如何使用规则数据  
 该规则从 Windows 性能监视设备中收集此度量数据，并报告此数据以仅供参考。  使用此规则可以比较程序的不同版本或内部版本的性能，或者了解不同测试方案中应用程序的性能。  
  
 双击“错误列表”窗口中的该消息以导航到分析数据的[“标记”视图](../profiling/marks-view.md)。  查找**“Process\\Working Set”**和**“Memory\\Pages\/sec”**计数器列。  然后查找**“Process\\Working Set”**的最大值并将其与**“Memory\\Pages\/sec”**值相比较。  通常，工作集的最大值与分页 IO 活动发生减少的时间间隔相关联，特别是在计算机受内存约束的情况下更是如此。