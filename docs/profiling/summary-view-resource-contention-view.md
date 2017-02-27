---
title: "“摘要”视图 - 探查器资源争用视图 | Microsoft Docs"
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
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# “摘要”视图 - 探查器资源争用视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“摘要”视图显示有关线程或进程等待访问资源时将其挂起的应用程序中事件的信息。  
  
 有关更多信息（包括通知链接和报告列表的说明），请参见[“摘要”视图](../profiling/summary-view.md)。  
  
## 时间线图  
 “摘要”视图中的时间线图显示被分析的应用程序在进行分析的这段时间内的争用事件数。  可以使用时间线图筛选所选时间跨度的视图。  有关更多信息，请参见 [如何：从摘要时间线中筛选报告视图](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 争用最激烈的资源  
 **“争用最激烈的资源”**列出了应用程序中导致最多争用事件的资源。  单击资源名称即可显示“争用”视图。  “争用”视图按线程提供资源争用的详细时间线。  
  
 **“争用最激烈的资源”**包括每个资源的以下数据。  
  
|列|说明|  
|-------|--------|  
|**名称**|资源名。|  
|**争用数百分比**|对此资源的争用数占分析数据期间所有争用事件数的百分比。|  
  
## 争用最激烈的线程  
 **“争用最激烈的线程”**列出了应用程序中具有最多争用事件的线程。  单击线程名称即可显示按线程提供资源争用的详细时间线的“争用”视图。  
  
 **“争用最激烈的线程”**包括每个线程的以下数据。  
  
|列|说明|  
|-------|--------|  
|**ID**|线程标识符。|  
|**名称**|拥有该线程的进程的名称。|  
|**争用数百分比**|对此资源的争用数占分析数据期间所有争用事件数的百分比。|