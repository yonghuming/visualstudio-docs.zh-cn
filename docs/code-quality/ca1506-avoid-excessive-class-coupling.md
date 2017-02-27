---
title: "CA1506：避免过度类耦合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1506：避免过度类耦合
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|类别|Microsoft.Maintainability|  
|是否重大更改|是|  
  
## 原因  
 类型或方法与其他很多类型耦合。  
  
## 规则说明  
 此规则通过计算类型或方法包含的唯一类型引用的个数来衡量类耦合。  
  
 具有高度类耦合的类型和方法很难维护。  最好是采用低耦合、高内聚的类型和方法。  
  
## 如何解决冲突  
 若要修复此冲突，请重新设计类型或方法，降低与之耦合的类型的数目。  
  
## 何时禁止显示警告  
 如果类型或方法虽然依赖大量其他类型，但仍被视为可维护，则排除此警告。  
  
## 请参阅  
 [维护性警告](../code-quality/maintainability-warnings.md)   
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)