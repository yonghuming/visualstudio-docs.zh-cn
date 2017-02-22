---
title: "使用探查器命令行收集独立应用程序的统计信息 | Microsoft Docs"
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
  - "采样分析方法"
  - "分析工具, 采样方法"
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用探查器命令行收集独立应用程序的统计信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节介绍通过从命令行使用采样方法为客户端（独立）应用程序收集性能统计信息的过程和选项。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见[分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**使用分析工具启动应用程序**|-   [如何：启动独立应用程序并收集应用程序统计信息](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**将探查器关联到正在运行的 .NET Framework 应用程序**|-   [如何：将探查器附加到 .NET Framework 应用程序并收集应用程序统计信息](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**将探查器附加到正在运行的 C\/C\+\+ 应用程序**|-   [如何：将探查器附加到本机应用程序并收集应用程序统计信息](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)|  
|**添加层交互数据**|-   [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## 相关任务  
  
### 分析独立应用程序  
  
|任务|相关内容|  
|--------|----------|  
|**检测应用程序**|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**收集 .NET 内存分配和垃圾回收数据**|-   [收集 .NET Framework 内存数据](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**收集资源争用和线程执行数据**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### 使用采样方法分析  
  
|任务|相关内容|  
|--------|----------|  
|**分析 ASP.NET Web 应用程序**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**分析服务**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md).  介绍如何使用采样方法从 Windows 服务收集性能统计信息。|  
  
### 分析采样数据视图和报告  
 [采样方法数据视图](../profiling/profiler-sampling-method-data-views.md)