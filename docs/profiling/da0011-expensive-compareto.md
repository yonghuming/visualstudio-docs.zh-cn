---
title: "DA0011：高开销的 CompareTo | Microsoft Docs"
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
  - "vs.performance.DA0011"
  - "vs.performance.rules.DAExpensiveCompareTo"
  - "vs.performance.11"
  - "vs.performance.rules.DA0011"
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0011：高开销的 CompareTo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0011|  
|类别|.NET Framework 使用|  
|分析方法|采样<br /><br /> .NET 内存|  
|消息|CompareTo 函数应是廉价的，并且不应分配任何内存。  如果可能，降低 CompareTo 函数的复杂性。|  
|规则类型|警告|  
  
## 原因  
 类型的 CompareTo 方法开销巨大或分配内存。  
  
## 规则说明  
 CompareTo 方法应效率很高，不应分配内存。  
  
## 如何解决冲突  
 降低 CompareTo 方法的复杂性。