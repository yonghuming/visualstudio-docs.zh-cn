---
title: "使用探查器采样方法收集服务的应用程序统计信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用探查器采样方法收集服务的应用程序统计信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节介绍一些过程和选项，用于从命令行使用采样方法收集 Windows 服务的性能统计信息。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**将探查器附加到 .NET 服务**|-   [如何：将探查器附加到 .NET 服务以收集应用程序统计信息](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**添加层交互数据**|-   [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**将探查器附加到 C\/C\+\+ 服务**|-   [如何：将探查器附加到本机服务以收集应用程序统计信息](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## 相关任务  
  
### 分析 Windows 服务  
  
|任务|相关内容|  
|--------|----------|  
|**使用检测方法分析**|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**分析 .NET 内存分配和垃圾回收**|-   [收集 .NET 内存数据](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**分析资源争用和线程活动**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### 使用采样方法分析  
  
|任务|相关内容|  
|--------|----------|  
|**分析独立（客户端）应用程序**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**分析 ASP.NET Web 应用程序**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
  
### 分析采样数据视图和报告  
 [采样方法数据视图](../profiling/profiler-sampling-method-data-views.md)