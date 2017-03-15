---
title: "使用探查器命令行收集服务的并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 使用探查器命令行收集服务的并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的并发方法，可以收集资源争用数据和线程活动数据，这些数据显示 CPU 使用率、线程争用、线程迁移、同步延迟、重叠 IO 的区域以及其他系统事件。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**附加到正在运行的 .NET 服务**|-   [如何：将探查器附加到 .NET 服务以收集并发数据](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**添加层交互数据**|-   [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**附加到正在运行的 C\/C\+\+ 服务**|-   [如何：将探查器附加到本机服务以收集并发数据](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## 相关任务  
  
### 分析 Windows 服务  
  
|任务|相关内容|  
|--------|----------|  
|**使用采样方法分析**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**使用检测方法分析**|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**分析 .NET 内存分配和垃圾回收**|-   [收集 .NET 内存数据](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### 分析并发数据  
  
|任务|相关内容|  
|--------|----------|  
|**分析独立应用程序**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**分析 ASP.NET Web 应用程序**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### 分析并发数据视图和报告  
 [资源争用数据视图](../profiling/resource-contention-data-views.md)  
  
 [并发可视化工具](../profiling/concurrency-visualizer.md)  
  
## 引用  
 [命令行分析工具参考](../profiling/command-line-profiling-tools-reference.md)