---
title: "了解分析工具中的资源争用数据值 | Microsoft Docs"
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
  - "并发分析方法"
  - "分析工具, 并发方法"
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 了解分析工具中的资源争用数据值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

资源争用分析收集每次应用程序中的争用线程访问共享资源时被强制等待的详细调用堆栈信息。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 资源争用报告将显示争用的总次数，以及发生等待的模块、函数、源代码行和指令等待资源所用的总时间。  
  
-   非独占值显示由于资源争用而迫使某函数等待的争用总次数，以及该函数等待的总时间。由该函数调用的子函数所导致的争用次数包含在非独占值中。  
  
-   独占值仅显示迫使某函数等待的争用的次数，以及由该函数体中的代码导致的争用次数。  子函数导致的争用次数不包括在内。  该函数的独占时间也只包括函数体中的语句导致的等待时间。  
  
 资源争用报告视图还包括时间线图，这些图显示一段时间内的单个争用事件以及创建特定事件的调用堆栈。  有关更多信息，请参见下列主题之一：  
  
-   [“线程详细信息”视图](../profiling/thread-details-view-contention-data.md)  
  
-   [“资源详细信息”视图](../profiling/resource-details-view-contention-data.md)  
  
 有关并发分析第二种模式的更多信息，请参见[并发可视化工具](../profiling/concurrency-visualizer.md)。