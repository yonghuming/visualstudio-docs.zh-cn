---
title: "DA0505：为所分析进程分配的平均专用字节数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0505"
  - "vs.performance.rules.DA0505"
  - "vs.performance.505"
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0505：为所分析进程分配的平均专用字节数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0505|  
|类别|资源管理|  
|分析方法|全部|  
|消息|收集此信息的目的是仅供参考。  Process Private Bytes 计数器测量所分析进程分配的虚拟内存。  报告的值是根据所有测量时间间隔求得的平均值。|  
|规则类型|信息|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。  
  
## 规则说明  
 此消息报告进程当前已分配的以字节（专用字节）为单位的平均虚拟内存量。  专用字节表示由进程分配的虚拟内存位置，该虚拟内存位置仅可由运行在该进程中的线程访问。  
  
 对于 32 位计算机上运行的 32 位进程，进程地址空间专用部分的上限为 2 GB。  使用 [\/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini 开关，32 位进程最多可以获取 3 GB 的虚拟内存。  在 64 位计算机上运行的 32 位进程最多可以获取 4 GB 的专用虚拟内存。  
  
 在 64 位计算机上运行的 64 位进程最多可以获取 8 TB 的专用虚拟内存。  
  
 报告的值是根据所有测量时间间隔求得的平均值，在这些时间间隔中，正在分析的进程处于活动状态。  
  
 有关进程地址空间的更多信息，请参见“Windows Memory Management”（Windows 内存管理）文档中的 [Virtual Address Space](http://go.microsoft.com/fwlink/?LinkId=177832)（虚拟地址空间）。  
  
## 如何使用规则数据  
 使用报告的值可以比较程序的不同版本或内部版本的性能，或者了解不同分析方案中应用程序的性能。