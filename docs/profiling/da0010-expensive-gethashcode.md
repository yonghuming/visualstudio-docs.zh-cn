---
title: "DA0010：高开销 GetHashCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0010：高开销 GetHashCode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0010|  
|类别|.NET Framework 使用|  
|分析方法|采样<br /><br /> .NET 内存|  
|消息|GetHashCode 函数应是廉价的，并且不应分配任何内存。  如果可能，降低哈希代码函数的复杂性。|  
|消息类型|警告|  
  
## 原因  
 对该类型的 GetHashCode 方法的调用在分析数据中占很大比例或此方法分配内存。  
  
## 规则说明  
 哈希是一项用于快速定位大型集合中的某个特定项的技术。  因为哈希表可能非常大，而且必须支持很高比率的访问，所以哈希表应该极其有效。  此要求的含义是 .NET Framework 中的 GetHashCode 方法不应分配内存。  分配内存增加在垃圾回收器上的负载，并向潜在延迟公开该方法（如果这因分配请求而成为运行垃圾回收器的必要条件）。  
  
## 如何解决冲突  
 降低此方法的复杂性。