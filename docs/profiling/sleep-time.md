---
title: "睡眠时间 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "并发可视化工具, 睡眠时间"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 睡眠时间
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

时间线中的这些时间段与分类为睡眠的阻塞时间相关联。  睡眠类别意味着某线程自动放弃其逻辑内核并且不执行任何工作。  在此期间，已在并发可视化工具计数为睡眠的 API 中阻塞某线程。  `Sleep()` 和 `SwitchToThread()` 等 API 就属于这一组。  
  
## 请参阅  
 [线程视图](../profiling/threads-view-parallel-performance.md)