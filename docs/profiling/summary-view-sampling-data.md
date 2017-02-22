---
title: "“摘要”视图 - 探查器采样数据 | Microsoft Docs"
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
  - "采样分析方法, “摘要”视图"
  - "“摘要”视图"
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “摘要”视图 - 探查器采样数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“摘要”视图显示有关分析运行期间性能代价最高的函数的信息。  有关更多信息（包括通知链接和报告列表的说明），请参见[“摘要”视图](../profiling/summary-view.md)。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 时间线图  
 “摘要”视图中的时间线图显示被分析的应用程序在进行分析的这段时间内的处理器 \(CPU\) 使用率的百分比。  可以使用时间线图筛选所选时间跨度的视图。  有关更多信息，请参见[如何：从摘要时间线中筛选报告视图](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 热路径  
 **“热路径”**显示从中收集了大多数样本的执行路径。  单击函数可以显示函数的“函数详细信息”视图。  若要显示函数的其他视图，请右击该函数，然后从列表中单击某个视图。  
  
 **“热路径”**包括每个函数的以下数据：  
  
|列|描述|  
|-------|--------|  
|**名称**|函数名。|  
|**非独占样本数百分比**|此函数或此函数调用的函数在执行时产生的所有样本数的百分比。|  
|**独占样本数 %**|函数在执行函数体内的代码时产生的所有样本数的百分比。  不包括此函数调用的各个函数中收集的样本。|  
  
## 执行单个工作最多的函数  
 **“执行单个工作最多的函数”**列表显示分析运行期间具有最大数量的独占样本的函数。  如果在收集样本时函数正在执行其自己的代码，则向该函数分配独占样本。  如果在收集样本时函数正在调用另一个函数，则不向该函数分配独占样本。  大量独占样本表示函数自身使用了大量时间。  
  
 单击函数可以显示函数的“函数详细信息”视图。  若要显示函数的其他视图，请右击该函数，然后从列表中单击某个视图。  
  
 **“执行单个工作最多的函数”**包括每个函数的以下数据：  
  
|列|描述|  
|-------|--------|  
|**名称**|函数名。|  
|**独占样本数 %**|函数执行其函数体内的代码时收集的样本数占分析运行期间所有样本数的百分比。  执行此函数所调用的函数时收集的独占样本数的百分比。|  
  
## 请参阅  
 [“摘要”视图](../profiling/summary-view-dotnet-memory-data.md)   
 [“摘要”视图](../profiling/summary-view-instrumentation-data.md)