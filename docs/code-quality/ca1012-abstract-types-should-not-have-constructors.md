---
title: "CA1012：抽象类型不应具有构造函数 | Microsoft Docs"
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
  - "AbstractTypesShouldNotHaveConstructors"
  - "CA1012"
helpviewer_keywords: 
  - "CA1012"
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1012：抽象类型不应具有构造函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 公共类型为抽象类型，并具有公共构造函数。  
  
## 规则说明  
 抽象类型的构造函数只能由派生类型调用。  由于公共构造函数用于创建类型的实例，但无法为抽象类型创建实例，因此具有公共构造函数的抽象类在设计上是错误的。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将构造函数设为受保护的构造函数，或者不要将类型声明为抽象类型。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  抽象类型具有公共构造函数。  
  
## 示例  
 下面的示例包含一个与此规则冲突的抽象类型。  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-cs[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## 示例  
 下面的示例通过将构造函数的可访问性从 `public` 更改为 `protected` 修复了前面的冲突。  
  
 [!code-cs[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]