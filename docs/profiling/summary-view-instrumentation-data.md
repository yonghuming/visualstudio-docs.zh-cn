---
title: "“摘要”视图 - 探查器检测数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“摘要”视图"
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# “摘要”视图 - 探查器检测数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“摘要”视图显示有关分析运行期间性能代价最高的函数的信息。  有关更多信息（包括通知链接和报告列表的说明），请参见[“摘要”视图](../profiling/summary-view.md)。  
  
## 时间线图  
 “摘要”视图中的时间线图显示被分析的应用程序在进行分析的这段时间内的处理器 \(CPU\) 使用率。  可以使用时间线图筛选所选时间跨度的视图。  有关更多信息，请参见 [如何：从摘要时间线中筛选报告视图](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 热路径  
 **“热路径”**显示用时最多的执行路径。  单击函数可以显示函数的“函数详细信息”视图。  若要显示函数的其他视图，请右击该函数，然后从列表中单击某个视图。  
  
 **“热路径”**包括每个函数的以下数据：  
  
|列|说明|  
|-------|--------|  
|**名称**|函数名。|  
|**已用非独占时间百分比**|函数执行其函数体内及其所调用的函数内的代码所用时间占分析数据所用总时间的百分比。|  
|**已用独占时间百分比**|函数执行其函数体内的代码所用时间占分析数据所用总时间的百分比。  不包括函数所调用的函数所用的时间。|  
  
## 大部分时间单独工作的函数  
 大部分时间执行函数体内的代码而非其所调用函数内的代码的函数的列表。  
  
 **“大部分时间单独工作的函数”**包括每个函数的以下数据：  
  
|列|说明|  
|-------|--------|  
|**名称**|函数名。|  
|**独占时间百分比**|函数执行其函数体内的代码所用时间占分析数据所用总时间的百分比。  不包括函数所调用的函数所用的时间。|  
  
## 请参阅  
 [“摘要”视图](../profiling/summary-view-sampling-data.md)   
 [“摘要”视图](../profiling/summary-view-dotnet-memory-data.md)