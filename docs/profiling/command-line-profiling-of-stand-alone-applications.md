---
title: "从命令行分析独立应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析工具, 独立应用程序"
  - "分析独立应用程序"
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 从命令行分析独立应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节介绍从命令行使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具为独立（客户端）应用程序收集性能数据的过程和选项。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**收集应用程序统计信息：**使用采样方法收集性能统计信息。  在分析 CPU 利用率问题，以及了解应用程序的常规性能特征时，会用到采样数据。|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**收集详细的计时数据：**使用检测方法收集详细的计时信息。  在分析 I\/O 问题，及精细分析应用程序的情形中，检测数据很有用。|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**收集 .NET 内存数据：**使用采样或检测方法收集 .NET 内存分配数据，这些数据显示已分配对象的大小和数目。  您还可以收集对象生存期数据，这些数据显示每代垃圾回收中所回收的对象的大小和数目。|-   [收集 .NET Framework 内存数据](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**收集并发数据：**使用并发方法收集资源争用数据和线程活动数据，这些数据显示 CPU 利用率、线程争用、线程迁移、同步延迟、I\/O 重叠区域和其他系统事件。|-   [收集并发数据](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**添加层交互数据：**可以添加有关应用程序对 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 数据库所做的同步 ADO.NET 调用的性能数据。  将层交互数据添加到运行的分析需要使用分析工具的特定程序。|-   [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**尝试：**使用采样或检测方法，按照分步过程分析示例客户端应用程序。|-   [演练：使用采样进行命令行分析](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)<br />-   [演练：使用检测进行命令行分析](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## 相关任务  
  
|任务|相关内容|  
|--------|----------|  
|**分析 ASP.NET 应用程序**|-   [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**分析服务**|-   [分析服务](../profiling/command-line-profiling-of-services.md)|