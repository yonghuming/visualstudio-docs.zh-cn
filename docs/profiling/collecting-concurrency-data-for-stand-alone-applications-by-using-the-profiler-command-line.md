---
title: "使用探查器命令行收集独立应用程序的并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "并发分析方法"
  - "分析工具，并发方法"
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用探查器命令行收集独立应用程序的并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的并发方法，可以收集资源争用数据和线程活动数据，这些数据显示 CPU 使用率、线程争用、线程迁移、同步延迟、重叠 IO 的区域以及其他系统事件。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**启动 .NET Framework 应用程序并分析并发数据**|-   [如何：启动 .NET Framework 应用程序以收集并发数据](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**启动 C\/C\+\+ 应用程序并分析并发数据**|-   [如何：启动本机应用程序以收集并发数据](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**将探查器关联到正在运行的 .NET Framework 应用程序**|-   [如何：将探查器附加到 .NET Framework 应用程序以收集并发数据](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**将探查器附加到正在运行的 C\/C\+\+ 应用程序**|-   [如何：将探查器附加到本机应用程序中并收集并发数据](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)|  
  
## 相关任务  
  
### 分析独立应用程序  
  
|任务|相关内容|  
|--------|----------|  
|**使用采样方法分析**|-   [使用采样法收集应用程序统计信息](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**使用检测方法分析**|-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**分析 .NET 内存分配和垃圾回收**|-   [收集 .NET Framework 内存数据](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**添加层交互数据**|-   [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### 分析并发问题  
  
|任务|相关内容|  
|--------|----------|  
|**分析 ASP.NET 应用程序**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**分析服务**|-   [收集并发数据](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### 分析并发数据视图和报告  
 [资源争用数据视图](../profiling/resource-contention-data-views.md)  
  
 [并发可视化工具](../profiling/concurrency-visualizer.md)  
  
## 引用  
 [命令行分析工具参考](../profiling/command-line-profiling-tools-reference.md)