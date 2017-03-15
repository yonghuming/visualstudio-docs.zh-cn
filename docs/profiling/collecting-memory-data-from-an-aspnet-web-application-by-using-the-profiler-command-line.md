---
title: "使用探查器命令行从 ASP.NET Web 应用程序收集内存数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 内存分析方法"
  - "分析工具, .NET 内存方法"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用探查器命令行从 ASP.NET Web 应用程序收集内存数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节介绍通过使用 **VSPerfCmd** 命令行工具收集 ASP.NET Web 应用程序的内存分配数据和对象生存期数据的过程和选项。  
  
> [!NOTE]
>  **VSPerfCmd** 工具为您提供对分析工具功能的完全访问权限，包括暂停和继续分析以及收集来自处理器和 Windows 性能计数器的更多数据。  如果您不需要此功能，也可以使用 **VSPerfASPNETCmd** 命令行工具。  与 [VSPerfCmd](../profiling/vsperfcmd.md) 命令行工具相比，它无需设置任何环境变量，也无需重新启动计算机。  有关更多信息，请参见[使用 VSPerfASPNETCmd 进行快速网站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**将探查器附加到正在运行的 ASP.NET 应用程序**|-   [如何：将探查器附加到 ASP.NET Web 应用程序以收集内存数据](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**检测静态编译的二进制文件**|-   [如何：检测静态编译的 ASP.NET 应用程序并收集内存数据](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**检测动态编译的二进制文件**|-   [如何：检测动态编译的 ASP.NET 应用程序并收集内存数据](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## 相关任务  
  
### 分析 ASP.NET Web 应用程序  
  
|任务|相关内容|  
|--------|----------|  
|**使用采样方法分析**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**使用检测方法分析**|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**分析资源争用和线程活动**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### 分析 .NET Framework 内存数据  
  
|任务|相关内容|  
|--------|----------|  
|**分析独立（客户端）应用程序**|-   [收集 .NET Framework 内存数据](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**分析服务**|-   [收集 .NET 内存数据](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### 分析 .NET 内存数据视图和报告  
 [.NET 内存数据视图](../profiling/dotnet-memory-data-views.md)  
  
## 引用  
 [命令行分析工具参考](../profiling/command-line-profiling-tools-reference.md)