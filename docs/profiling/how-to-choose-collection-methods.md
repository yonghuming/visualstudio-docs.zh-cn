---
title: "如何：选择收集方法 | Microsoft Docs"
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
  - "性能工具, 选择收集方法"
  - "分析工具, 选择收集方法"
  - "性能集合方法"
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：选择收集方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具支持三种收集性能数据的方法，即采样、检测和并发。  也可以使用采样或检测方法来收集 .NET 内存分配和生存期数据。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 可以使用性能会话的**“方法”**属性为应用程序指定最合适的收集方法。  可以从性能向导、性能资源管理器或性能会话的属性页设置收集方法。  如果您正在使用命令行工具，请参见[通过命令行进行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)获取更多信息。  
  
## 性能向导  
  
#### 使用性能向导选择收集方法  
  
-   在向导的第一页上，选择下列选项之一：  
  
|选项|说明|  
|--------|--------|  
|**CPU 采样**|收集应用程序统计信息，这些信息可用于初始分析和 CPU 利用率问题分析。|  
|**检测**|收集详细的计时数据，这些数据可用于重点分析和输入\/输出性能问题分析。|  
|**.NET 内存分配**|使用采样分析方法收集 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 内存分配数据。|  
|**并发**|可以收集资源争用数据。|  
  
## 性能资源管理器  
  
#### 使用性能资源管理器选择收集方法  
  
1.  在**“性能资源管理器”**工具栏上，单击**“方法”**下拉列表旁的箭头。  
  
2.  单击您喜欢的收集方法。  
  
## 性能会话属性页  
  
#### 使用性能会话属性选择采样或检测方法  
  
1.  在**“性能资源管理器”**中，选择性能会话。  
  
     性能会话文件名带 .psess 扩展名。  
  
2.  右击该性能会话，然后单击**“属性”**。  
  
3.  在**“属性页”**中，单击**“常规”**。  
  
4.  单击您喜欢的收集方法。  
  
    -   有关收集采样数据时可用的其他选项的信息，请参见[使用采样收集性能统计信息](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   有关收集采用数据时可用的其他选项的信息，请参见[使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)。  
  
#### 使用性能会话属性选择 .NET 内存数据收集  
  
1.  在**“性能资源管理器”**中，选择性能会话。  
  
     性能会话文件名带 .psess 扩展名。  
  
2.  右击该性能会话，然后单击**“属性”**。  
  
3.  在**“属性页”**中，单击**“常规”**。  
  
4.  单击**“采样”**或**“检测”**。  
  
5.  单击**“收集 .NET 对象分配信息”**以收集 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 对象分配的大小和数量。  
  
6.  （可选）单击**“同时收集 .NET 对象的生存期信息”**以收集有关用来回收对象内存的垃圾回收代的数据。  
  
     有关收集 .NET 内存数据时可用的其他选项的信息，请参见[收集 .NET 内存分配数据和生存期数据](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)。  
  
#### 使用性能会话属性选择并发数据收集  
  
1.  在**“性能资源管理器”**中，右击性能会话，然后单击**“属性”**。  
  
2.  在**“属性页”**中，单击**“常规”**。  
  
3.  单击**“并发”**。  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [了解采样数据值](../profiling/understanding-sampling-data-values.md)   
 [性能会话属性](../profiling/performance-session-properties.md)