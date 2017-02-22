---
title: "空时间线分段 | Microsoft Docs"
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
  - "vs.cv.threads.timeline.empty"
helpviewer_keywords: 
  - "并发可视化工具, 空时间线分段"
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 空时间线分段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在并发可视化工具中，时间线的部分为空 \(具有白色背景\)的原因 取决于这种通道。  
  
-   对于线程 CPU 通道，意味着在时间线的这一部分，线程不存在。  如果您需要查看线程，则可以使用缩放控件或水平滚动条来查找其执行部分。  
  
-   对于一个 I\/O 通道，意味着在那个点的一半目标进程下访问磁盘没有及时发生。  
  
-   对于 DirectX 通道，意味着在时间线的这一部分，GPU 工作未代表目标进程运行。  
  
-   对于标记通道，意味着标记尚未生成。  
  
## 请参阅  
 [线程视图](../profiling/threads-view-parallel-performance.md)   
 [缩放控件（线程视图）](../profiling/zoom-control-threads-view.md)