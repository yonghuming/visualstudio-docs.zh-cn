---
title: "从命令行使用探查器检测方法收集 ASP.NET Web 应用程序的详细计时数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "检测分析方法"
  - "分析工具, 检测方法"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 从命令行使用探查器检测方法收集 ASP.NET Web 应用程序的详细计时数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节介绍通过使用 **VSPerfCmd** 命令行工具和检测方法收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序的详细性能数据的过程和选项。  
  
> [!NOTE]
>  **VSPerfCmd** 工具为您提供对分析工具功能的完全访问权限，包括暂停和继续分析以及收集来自处理器和 Windows 性能计数器的更多数据。  如果您不需要此功能，也可以使用 **VSPerfASPNETCmd** 命令行工具。  与 [VSPerfCmd](../profiling/vsperfcmd.md) 命令行工具相比，无需设置任何环境变量，也无需重新启动计算机。  有关更多信息，请参见[使用 VSPerfASPNETCmd 进行快速网站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**分析静态编译的二进制文件**|-   [如何：检测静态编译的 ASP.NET 应用程序并收集详细计时数据](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**分析动态编译的二进制文件**|-   [如何：检测动态编译的 ASP.NET 应用程序并收集详细计时数据](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)|  
  
## 相关任务  
  
### 分析 ASP.NET Web 应用程序  
  
|任务|相关内容|  
|--------|----------|  
|**使用采样方法分析**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**分析内存分配和垃圾回收**|-   [收集内存数据](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**分析资源争用和线程活动**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### 使用检测方法分析  
  
|任务|相关内容|  
|--------|----------|  
|**分析独立（客户端）应用程序**|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**分析服务**|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### 分析检测数据视图和报告  
 [检测方法数据视图](../profiling/instrumentation-method-data-views.md)