---
title: "服务的命令行分析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析工具，服务"
  - "分析服务"
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 服务的命令行分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节介绍从命令行使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具为 Windows 服务收集性能数据的过程和选项。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**收集应用程序统计信息：**使用采样方法收集性能统计信息。  在分析 CPU 利用率问题，以及了解应用程序的常规性能特征时，会用到采样数据。|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**收集详细的计时数据：**使用检测方法收集详细的计时信息。  在分析 IO 问题，及精细分析应用程序的情形中，检测数据很有用。|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**收集 .NET 内存数据：**使用采样或检测方法收集 .NET 内存分配数据，这些数据显示已分配对象的大小和数目。  您还可以收集对象生存期数据，这些数据显示每代垃圾回收中所回收的对象的大小和数目。|-   [收集 .NET 内存数据](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**收集并发数据：**使用并发方法收集资源争用数据和线程活动数据，这些数据显示 CPU 利用率、线程争用、线程迁移、同步延迟、IO 重叠区域和其他系统事件。|-   [收集并发数据](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**添加层交互数据：**可以添加有关服务对 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 数据库所做的同步 ADO.NET 调用的性能数据。|-   [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## 相关任务  
  
|任务|相关内容|  
|--------|----------|  
|**分析独立（客户端）应用程序**|-   [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**分析 ASP.NET 应用程序**|-   [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)|