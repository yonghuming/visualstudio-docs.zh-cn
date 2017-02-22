---
title: "同步时间 | Microsoft Docs"
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
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "并发可视化工具, 同步时间"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 同步时间
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

时间线中的这些时间段与被分类为同步的阻塞时间相关联。  当线程被标记为在同步中阻塞时，暗示出现了下列情况之一：  
  
-   执行该线程可能导致调用已知线程同步 API（如 `EnterCriticalSection()` 或 `WaitForSingleObject()`）。  
  
-   API 匹配算法无法做到非常全面，因此一些可映射到其他类别的 API 也可能显示为同步，这是因为调用堆栈中的帧会逐渐到达映射到此类别的基础内核阻止基元。  
  
 通过仔细检查阻塞调用堆栈和分析报告，可以了解线程阻塞事件的基本原因。  
  
## 请参阅  
 [线程视图](../profiling/threads-view-parallel-performance.md)