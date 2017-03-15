---
title: "“摘要”视图 - 探查器 .NET 内存数据 | Microsoft Docs"
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
  - "“摘要”视图"
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “摘要”视图 - 探查器 .NET 内存数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“摘要”视图显示有关分配了最多内存的 .NET 函数和类型以及分析运行期间大多数时间所创建的类型的信息。  有关更多信息（包括通知链接和报告列表的说明），请参见[“摘要”视图](../profiling/summary-view.md)。  
  
## 时间线图  
 “摘要”视图中的时间线图显示被分析的应用程序在进行分析的这段时间内的处理器 \(CPU\) 使用率。  可以使用时间线图筛选所选时间跨度的视图。  有关详细信息，请参阅[如何：从摘要时间线中筛选报告视图](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 分配最多内存的函数  
 列出在分析运行期间分配了最大字节数内存的函数。  
  
|列|说明|  
|-------|--------|  
|**名称**|函数名。|  
|**字节数百分比**|在分析运行期间分配的，此函数或其调用的子函数所分配的所有字节数的百分比。|  
  
## 内存分配最多的类型  
 列出分析运行期间为其分配了最大字节数的内存的类型。  
  
|列|说明|  
|-------|--------|  
|**名称**|类型名称。|  
|**字节数百分比**|为此类型分配的字节数占分析运行期间全部所分配字节数的百分比。|  
  
## 实例最多的类型  
 列出在分析 run. had 期间创建次数最多的类型。  
  
|列|说明|  
|-------|--------|  
|**名称**|类型名称。|  
|**实例数百分比**|此类型的实例占分析运行期间创建的 .NET 对象总数的百分比。|  
  
## 请参阅  
 [“摘要”视图](../profiling/summary-view-sampling-data.md)   
 [“摘要”视图](../profiling/summary-view-instrumentation-data.md)