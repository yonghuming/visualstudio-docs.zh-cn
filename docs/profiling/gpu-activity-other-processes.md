---
title: "GPU 活动(其他进程) | Microsoft Docs"
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
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GPU 活动(其他进程)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当 GPU 代表系统上的其他进程处理请求时，在并发可视化工具的线程视图的 **GPU 活动 \(其他进程\)** 时间段表示。  这些请求发送GPU 作为直接内存存取 \(DMA\) 数据包。段的长度代表数据包的 GPU 处理时间的持续时间。  
  
 当选择 这种活动段，则 当前  选项卡显示有关被处理的 DMA 数据包信息的报告。该信息包括与 DirectX 引擎关联的数据包在硬件队列中等待的总共时间，进程提交数据包以及需要的处理数据包的时间。