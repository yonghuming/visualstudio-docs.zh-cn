---
title: "使用分析工具控制数据收集 | Microsoft Docs"
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
  - "针对分析工具的高级任务"
  - "分析工具, 高级任务"
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用分析工具控制数据收集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具，可以控制在性能会话期间收集分析数据的时间以及指定分析的函数。  本节介绍如何从**“性能资源管理器”**和**“数据收集控件”**窗口启动和停止数据收集，以及如何限制为其收集分析数据的对象。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**启动和停止分析：**可以在应用程序启动时开始分析应用程序，也可以将探查器附加到已在运行的进程。  当目标应用程序正在运行时，可以暂停并继续数据收集。  通过关闭目标应用程序或从正在运行的进程中分离探查器，可以结束分析会话。|-   [如何：启动和结束分析](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [如何：在正在运行的进程中附加和分离探查器](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [如何：暂停和继续分析](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)|  
|**配置检测分析以限制收集的数据：**可以使用性能会话配置属性来限制在使用检测方法的分析运行中收集的数据。  您可以包括或排除特定的 .dll 文件、命名空间、类和函数。  也可以排除不满足您指定的大小阈值的函数。|-   [如何：将检测限定为特定 DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [如何：将检测限定为特定函数](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [如何：在检测中排除或包括短函数](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)|  
  
## 相关章节  
 [配置性能会话](../profiling/configuring-performance-sessions.md)  
  
## 请参阅  
 [使用分析工具](../profiling/performance-explorer.md)