---
title: "GPU 活动关系图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph.gpu"
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# GPU 活动关系图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在并发可视化工具的 GPU 活动图显示在系统级的 DirectX 活动。测量由的 DirectX 引擎数在一段时间内是在使用中。图不显示使用了哪些特定引擎。如果处理任意 GPU 工作，则引擎被认为在使用中。  
  
## GPU 活动图颜色  
 绿色由当前进程 DirectX 指示引擎的使用。  
  
 浅灰色由系统上其他进程 DirectX 指示引擎的使用。  若要减少其他进程DirectX 引擎的消耗，请减少其他系统上运行的进程数。  
  
 白色指示未使用的 DirectX 引擎状态的系统上。  如果可以找到更多开发机会，这些引擎将可用于您的进程。  引擎某些可用于特定类型任务仅使用。  
  
## 请参阅  
 [使用率视图](../profiling/utilization-view.md)