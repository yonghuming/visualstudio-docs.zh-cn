---
title: "DA0004：处理器使用率很高 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAHighProcessorUsage"
  - "vs.performance.rules.DA0004"
  - "vs.performance.DA0004"
  - "vs.performance.4"
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0004：处理器使用率很高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0004|  
|类别|分析工具使用|  
|分析方法|检测<br /><br /> 采样|  
|消息|您的处理器使用率始终大于 75%。  请考虑使用 CPU 绑定的应用程序的采样模式。|  
|规则类型|信息|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。  
  
## 原因  
 在使用检测方法收集的分析数据中，处理器 \(CPU\) 使用率相当高。  在分析受 CPU 限制的应用程序时，请考虑使用采样分析方法。  
  
## 规则说明  
 在此分析运行中，处理器（或多个处理器）始终很忙。  高 CPU 使用率可以指示 CPU 绑定的应用程序。  已检测的配置文件通常不是调查 CPU 使用方案的最有效的方法。  通常，在分析将大量时间花费在执行处理器指令的应用程序时，采样最为有效。  
  
## 如何解决冲突  
 请考虑使用采样方法而非检测方法再次分析应用程序，除非需要函数计时，或与处理器瓶颈相比更有兴趣了解输入\/输出。