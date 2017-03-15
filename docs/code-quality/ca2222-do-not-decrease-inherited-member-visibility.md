---
title: "CA2222：不要递减继承成员的可见性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2222：不要递减继承成员的可见性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 未密封类型中的私有方法所包含的签名与在基类型中声明的公共方法相同。  该私有方法不是最终方法。  
  
## 规则说明  
 不能更改所继承成员的访问修饰符。  将继承的成员更改为私有成员不能防止调用方访问该方法的基类实现。  如果将该成员设为私有但类型为非密封的，继承该成员的类型可以调用继承层次结构中该方法的上一次公共实现。  如果必须更改访问修饰符，则应将该方法标记为最终方法或将其类型设为密封的以防止重写该方法。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将访问修饰符更改为非私有修饰符。  如果您的编程语言支持，还可以将该方法设为最终方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]