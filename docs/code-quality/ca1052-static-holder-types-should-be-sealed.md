---
title: "CA1052：应密封静态容器类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1052：应密封静态容器类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 某公共或受保护类型仅包含静态成员，而且没有用 [sealed](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\) 修饰符声明。  
  
## 规则说明  
 该规则假定只包含静态成员的类型没有设计为能被继承，因为该类型不提供可以在派生类型中重写的任何功能。  不打算被继承的类型应该用 `sealed` 修饰符标记，以免作为基类型使用。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将该类型标记为 `sealed`。  如果针对的是 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 或更早版本，一个更好的方法是将该类型标记为 `static`。  在这种方法中，不必声明一个私有构造函数来防止创建类。  
  
## 何时禁止显示警告  
 只有当该类型旨在被继承时，才能禁止显示与该规则有关的警告。  没有 `sealed` 修饰符意味着该类型可以用作基类型。  
  
## 冲突的示例  
  
### 说明  
 下面的示例演示一个与该规则冲突的类型。  
  
### 代码  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## 使用 Static 修饰符进行修复  
  
### 说明  
 下面的示例演示如何通过使用 `static` 修饰符标记类型来修复此规则的冲突。  
  
### 代码  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## 相关规则  
 [CA1053：静态容器类型不应具有构造函数](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)