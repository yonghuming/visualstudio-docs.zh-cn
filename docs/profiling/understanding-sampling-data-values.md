---
title: "了解分析工具中的采样数据值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "采样分析方法"
  - "分析工具, 采样"
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# 了解分析工具中的采样数据值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的采样分析方法按设置的时间间隔中断计算机处理器并收集函数调用堆栈。  调用堆栈是一个动态结构，用于存储有关正在处理器上执行的函数的信息。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 探查器分析确定处理器是否正在执行目标进程中的代码。  如果处理器没有在执行目标进程中的代码，将放弃样本。  
  
 如果处理器正在执行目标代码，探查器将递增调用堆栈上每个函数的样本计数。  采样时，调用堆栈上只有一个函数当前正在执行代码。  堆栈上的其他函数都是函数调用层次结构中正在等待其子函数返回的父函数。  
  
 对于样本事件，探查器递增当前正在执行其指令的函数的独占样本计数。  由于独占样本也是函数的总（非独占）样本的一部分，因此还将累加当前活动函数的非独占样本数。  
  
 探查器递增调用堆栈上所有其他函数的非独占样本计数。  
  
## 非独占样本数  
 执行目标函数期间收集的样本总数。  
  
 这包括直接执行函数代码期间收集的样本和执行目标函数调用的子函数期间收集的样本。  
  
## 独占样本数  
 直接执行目标函数的指令期间收集的样本数。  
  
 独占样本不包括执行目标函数调用的函数期间收集的样本。  
  
## 非独占百分比  
 函数或数据范围的非独占样本占分析运行中非独占样本总数的百分比。  
  
## 独占百分比  
 函数或数据范围的独占样本占分析运行中独占样本总数的百分比。  
  
## 请参阅  
 [如何：选择收集方法](../profiling/how-to-choose-collection-methods.md)   
 [对分析工具数据进行分析](../profiling/analyzing-performance-tools-data.md)