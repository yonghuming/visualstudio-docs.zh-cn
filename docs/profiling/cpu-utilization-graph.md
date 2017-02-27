---
title: "CPU 使用率图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph"
helpviewer_keywords: 
  - "CPU 使用率图并行可视化工具, CPU 利用率图"
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# CPU 使用率图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CPU 使用率图显示一段时间内应用程序中的使用程度。  X 轴表示跟踪的持续时间，Y 轴表示系统上的逻辑内核数。  此图形不显示在某个给定时间有哪个特定内核是活动的。  举例来说，如果两个内核在某一给定时间段内均以 50% 的功率运行，那么此视图将显示正在使用一个逻辑内核。  
  
## CPU 使用率图颜色  
  
-   绿色表示系统中当前进程的逻辑核心利用率。  
  
-   浅灰表示系统上其他进程的逻辑内核利用率。  CPU中浅灰所占百分比高表示其他进程已使系统负载过重，您的进程可能会被这些进程抢占资源。  若要减少其他进程的逻辑内核消耗，请减少系统上运行的进程数。  
  
-   深灰色表示系统进程的逻辑内核消耗。  您无法直接控制这部分逻辑内核消耗，但由于这些消耗会影响您的进程可以使用的逻辑内核情况，因此了解这些消耗何时出现非常有用。  
  
-   白色表示系统上未使用逻辑内核的可用性。  如果可以找到更多并行机会，这些内核将可用于您的进程。  
  
## 请参阅  
 [使用率视图](../profiling/utilization-view.md)   
 [CPU 平均利用率](../profiling/average-cpu-utilization.md)