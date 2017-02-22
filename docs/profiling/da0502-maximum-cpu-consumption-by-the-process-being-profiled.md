---
title: "DA0502：所分析的进程的 CPU 最大消耗量 | Microsoft Docs"
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
  - "vs.performance.rules.DA0502"
  - "vs.performance.DA0502"
  - "vs.performance.502"
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0502：所分析的进程的 CPU 最大消耗量
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0502|  
|类别|资源监控|  
|分析方法|全部|  
|消息|此规则仅供参考。  Process\(\)\\% Processor Time 计数器测量所分析进程的 CPU 使用率。  报告的值是在所有测量时间间隔上观察到的最大值。|  
|规则类型|信息性|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。  
  
## 规则说明  
 此消息报告处理器忙于执行应用程序指令所用的时间的最大百分比。  报告的值是所有测量时间间隔中报告的最大值，在这些时间间隔中，正在分析的进程处于活动状态。  在具有多个处理器的计算机上，此百分比可以大于 100%。  
  
## 如何使用规则数据  
 使用此规则值可以比较程序的不同版本或内部版本的性能，或者了解不同分析方案中应用程序的性能。