---
title: "CA1809：避免过多的局部变量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1809：避免过多的局部变量
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 成员包含的局部变量超过 64 个，其中的某些变量可能是编译器生成的。  
  
## 规则说明  
 优化性能的常见方法是将值存储于处理器寄存器，而不是内存中，这称为*“注册值”*。  公共语言运行时最多可考虑注册 64 个局部变量。  未注册的变量放在堆栈中，必须移到寄存器内方能进行操作。  若要提供所有的局部变量都能注册的机会，应将局部变量的数目限制在 64 个以内。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请重构此实现，以确保使用的局部变量不超过 64 个。  
  
## 何时禁止显示警告  
 如果无需顾虑性能，可以安全地禁止显示此规则发出的警告，或者禁用此规则。  
  
## 相关规则  
 [CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)