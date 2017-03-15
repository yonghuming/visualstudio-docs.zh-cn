---
title: "CA1034：嵌套类型不应是可见的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1034：嵌套类型不应是可见的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见类型包含外部可见的类型声明。  嵌套枚举数和受保护的类型不受此规则限制。  
  
## 规则说明  
 嵌套类型是在另一个类型的范围中声明的类型。  嵌套类型用于封装包含类型的私有实现详细信息。  如果用于此用途，则嵌套类型不应是外部可见的。  
  
 不要将外部可见的嵌套类型用于逻辑分组或用于避免名称冲突；请改用命名空间。  
  
 嵌套类型包含成员可访问性的概念，不是所有的程序员都清楚了解该概念。  
  
 受保护的类型可用于高级自定义方案中的子类和嵌套类型。  
  
## 如何解决冲突  
 如果您不希望嵌套类型在外部可见，请更改该类型的可访问性。  否则，从嵌套类型的父类型中移除它。  如果嵌套的目的是对嵌套类型进行分类，请改为使用命名空间创建层次结构。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]