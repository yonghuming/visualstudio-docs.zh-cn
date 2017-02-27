---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**QueryCounters** 选项列出计算机上可用的 CPU（硬件）性能计数器。  
  
 **QueryCounters** 选项必须是命令行中的唯一选项。  
  
## 语法  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### 参数  
 无  
  
## 备注  
 使用检测方法时，探查器可以在每个数据收集事件中收集一个或多个 CPU 性能计数器的值。  使用采样分析方法时，可以指定一个计数器事件和要用作采样间隔的事件出现次数。  
  
 处理器不同，所公开的 CPU 性能计数器也不同。  探查器定义一组常规计数器，可用在几乎所有处理器上。  **QueryCounters** 选项同时列出常规计数器的名称和处理器专用计数器的名称。  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)