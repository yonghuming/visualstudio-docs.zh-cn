---
title: "CA1823：避免未使用的私有字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1823：避免未使用的私有字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 当代码中存在私有字段，但是任何代码路径都未使用它时，将报告此规则。  
  
## 规则说明  
 检测到程序集内有似乎未访问过的私有字段。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请移除该字段，或添加使用该字段的代码。  
  
## 何时禁止显示警告  
 可以安全地禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1812：避免未实例化的内部类](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801：检查未使用的参数](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)