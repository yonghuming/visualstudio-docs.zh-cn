---
title: "CA1804：移除未使用的局部变量 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1804：移除未使用的局部变量
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|RemoveUnusedLocals|  
|CheckId|CA1804|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 某方法声明一个局部变量，但除了将该变量作为赋值语句的接收者之外，并不使用该变量。  要通过该规则进行分析，必须使用调试信息生成被测试的程序集，并且关联的程序数据库 \(.pdb\) 文件必须可用。  
  
## 规则说明  
 未使用的局部变量和不必要的赋值会增加程序集的大小并降低性能。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请移除或使用局部变量。  注意，在启用了 `optimize` 选项的情况下，随 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 提供的 C\# 编译器将移除未使用的局部变量。  
  
## 何时禁止显示警告  
 如果变量是编译器发出的，则可以禁止显示此规则发出的警告。  如果性能和代码维护不是优先考虑的因素，则也可以安全地禁止显示此规则发出的警告，或者禁用此规则。  
  
## 示例  
 下面的示例演示一些未使用的局部变量。  
  
 [!CODE [FxCop.Performance.UnusedLocals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals#1)]  
  
## 相关规则  
 [CA1809：避免过多的局部变量](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812：避免未实例化的内部类](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801：检查未使用的参数](../Topic/CA1801:%20Review%20unused%20parameters.md)