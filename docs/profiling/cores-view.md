---
title: "内核视图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.cores"
helpviewer_keywords: 
  - "并发可视化工具, 内核视图"
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 内核视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

内核视图映射显示线程执行与逻辑处理器内核。  如果您正在编写服务器应用程序，则此视图可以帮助您通过使用线程关联或线程池管理来优化缓存性能。  如果在使用线程关联之后实际上加剧了跨内核迁移问题，则此视图还可帮助您以直观方式检查相关情况。  内核视图有两部分组成关系图和图例的。  
  
 图表在 Y 轴上显示逻辑内核，在 X 轴上显示时间。  该图表中的每个线程都具有唯一的颜色，以便您可以看到它随时间跨内核移动的情况。  您可以通过选中这些筛选此图的线程在图例区域。  
  
 图例区域具有每种颜色的项关系图中。  每个输入显示了线程颜色和名称、跨内核上下文切换的次数、上下文切换的总次数以及跨内核上下文切换次数的百分比。  该图例按跨内核上下文切换的次数降序排序。  它列在显示时间范围内，执行的线程。如果通过缩放或平移，列表被更新。  
  
## 请参阅  
 [并发可视化工具](../profiling/concurrency-visualizer.md)   
 [使用率视图](../profiling/utilization-view.md)   
 [线程视图](../profiling/threads-view-parallel-performance.md)