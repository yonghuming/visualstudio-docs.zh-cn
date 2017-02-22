---
title: "资源监控性能规则 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 资源监控性能规则
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

资源监控类别中的性能消息提供有关您的应用程序的性能的其他数据。  您可以使用此数据分析性能问题。  这些规则是每次分析运行报告的信息性消息。  
  
|||  
|-|-|  
|[DA0501：所分析的进程的平均 CPU 使用率。](../Topic/DA0501:%20Average%20CPU%20consumption%20by%20the%20Process%20being%20profiled..md)|此消息报告处理器忙于执行应用程序指令所用的时间的百分比。  报告的值是对所有测量时间间隔求得的平均值，在这些时间间隔中正在分析的进程处于活动状态。|  
|[DA0502：所分析的进程的 CPU 最大消耗量](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|此消息报告处理器忙于执行应用程序指令所用的时间的最大百分比。  报告的值是所有测量时间间隔中报告的最大值，在这些时间间隔中，正在分析的进程处于活动状态。|  
|[DA0503：所分析的进程的平均工作集\(以字节为单位\)](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|此消息报告分析处于活动状态时进程使用的平均物理内存量（以字节为单位）。  此物理内存度量值称作“工作集”。|  
|[DA0504：所分析的进程的最大工作集\(以字节为单位\)](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|此消息报告分析处于活动状态时进程使用的最大物理内存量（以字节为单位）。|  
|[DA0505：为所分析进程分配的平均专用字节数](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|此消息报告分析处于活动状态时进程分配的平均虚拟内存量（以字节为单位）。  此虚拟内存度量值称作“专用字节”。  专用字节表示由进程分配的虚拟内存位置，该虚拟内存位置仅可由运行在该进程中的线程访问。|  
|[DA0506：为所分析的进程分配的最大专用字节数](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|此消息报告分析处于活动状态时进程分配的最大虚拟内存量（以专用字节为单位）。|