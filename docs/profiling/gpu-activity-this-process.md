---
title: "GPU 活动(此进程) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuexecution"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# GPU 活动(此进程)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当 GPU 代表当前进程作为处理请求时，在并发可视化工具中的线程视图的 **GPU 活动 \(此过程\)** 时间段表示了显示时间。  这些请求发送到 GPU 作为直接内存存取 \(DMA\) 数据包。  段的长度代表 GPU 作为当前进程处理 DMA 数据包的时间。  
  
 当选择 GPU 活动段，则 **当前** 选项卡显示有关被处理的 DMA 数据包信息的报告。  此信息包括与 DirectX 引擎关联的数据包在硬件队列中等待的总共时间，进程提交数据包以及需要的处理数据包的时间。  除当前进程中的进程可以物理提交 DMA 数据包到 GPU。  并发可视化工具可检测当另一个进程代表当前进程提交的工作交给 GPU 时。