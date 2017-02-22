---
title: "CA1821：移除空的终结器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1821：移除空的终结器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 类型实现空终结器、只调用基类型终结器，或者只调用按条件发出的方法。  
  
## 规则说明  
 应尽可能避免终结器，因为跟踪对象生存期会产生额外的性能系统开销。  垃圾收集器将在收集该对象之前运行终结器。  这意味着收集该对象需要两个集合。  空的终结器只会徒增这种系统开销，而没有一点好处。  
  
## 如何解决冲突  
 移除空的终结器。  如果进行调试时需要一个终结器，请将整个终结器括在 `#if DEBUG / #endif` 指令中。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的消息。  如果取消终止失败，会使性能下降且不会有任何好处。  
  
## 示例  
 下面的示例演示应移除的空终结器、应括在 `#if DEBUG / #endif` 指令中的终结器和一个正确使用 `#if DEBUG / #endif` 指令的终结器。  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]