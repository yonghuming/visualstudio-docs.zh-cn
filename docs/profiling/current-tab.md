---
title: "当前选项卡 | Microsoft Docs"
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
  - "vs.cv.threads.reportnav.current"
helpviewer_keywords: 
  - "并发可视化工具, 选择点处的调用堆栈"
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 当前选项卡
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果 一个 CPU 线程被选中，通过单击 **“当前”** 选项卡，可以看到在时间线上与当前选择点最近的调用堆栈（如果有）。在这种情况下，选中点由时间线上的一个黑色箭头或插入符号表示。  如果选中了正在阻塞的片段，插入符号由于没有执行而没有显示。  但是，仍会显示突出段，以及调用堆栈。  
  
 **当前** 选项卡还显示有关 DirectX 活动段、标记和 I\/O 访问的信息。对于活动 DirectX 段，有关 DMA 数据包被硬件处理队列的方式的相关信息会被显示。对于标记，有关说明和类型标记的信息被显示。对于 I\/O 访问，有关文件和字节数的读取和写入的信息被显示。  
  
## 请参阅  
 [线程视图](../profiling/threads-view-parallel-performance.md)