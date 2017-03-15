---
title: "内存管理时间 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.paging"
helpviewer_keywords: 
  - "并发可视化工具，分页时间"
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 内存管理时间
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

时间线中的这些时间段与被分类为内存管理的阻塞时间相关联。  这意味着线程被与内存管理操作（如，分页）相关联的事件阻塞。  在此期间，某个线程已在并发可视化工具将其视为内存管理的 API 或内核状态中被阻塞。  其中包括分页和内存分配等事件。  
  
 检查关联的调用堆栈和配置文件报告，以更好地了解阻塞属于内存管理类别的基本原因。  
  
## 请参阅  
 [线程视图](../profiling/threads-view-parallel-performance.md)