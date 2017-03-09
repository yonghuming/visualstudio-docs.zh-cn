---
title: "CA1036：重写可比较类型中的方法 | Microsoft Docs"
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
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036：重写可比较类型中的方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 公共或受保护类型实现 <xref:System.IComparable?displayProperty=fullName> 接口，不重写 <xref:System.Object.Equals%2A?displayProperty=fullName>，也不重载表示相等、不等、小于或大于的语言特定的运算符。  如果该类型仅继承接口的实现，则该规则不会报告冲突。  
  
## 规则说明  
 定义自定义排序顺序的类型实现 <xref:System.IComparable> 接口。  <xref:System.IComparable.CompareTo%2A> 方法返回一个整数值，指示该类型的两个实例的正确排序顺序。  该值标识设置排序顺序的类型；这意味着不会应用相等、不等、小于或大于的常规含义。  提供 <xref:System.IComparable> 的实现时，通常还必须重写 <xref:System.Object.Equals%2A>，以使其返回与 <xref:System.IComparable.CompareTo%2A> 一致的值。  如果重写 <xref:System.Object.Equals%2A> 并使用支持运算符重载的语言编写代码，则还应提供与 <xref:System.Object.Equals%2A> 一致的运算符。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请重写 <xref:System.Object.Equals%2A>。  如果您的编程语言支持运算符重载，请提供下列运算符：  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 在 C\# 中，用来代表这些运算符的标记如下所示: \=\=, \!\=, \<, and \>.  
  
## 何时禁止显示警告  
 如果冲突是因缺少运算符引起的，且您的编程语言不支持运算符重载（例如，在 Visual Basic .NET 中就是这样），则可以安全地禁止显示此规则发出的警告。  如果您确定实现相等运算符在应用程序上下文中没有意义，则当 op\_Equality 以外相等运算符上激发此规则时，禁止此规则的显示也是安全的。  但是，如果重写 Object.Equals，应该始终重写 op\_Equality 和 \=\= 运算符。  
  
## 示例  
 下面的示例包含正确实现 <xref:System.IComparable> 的类型。  代码注释标识满足与 <xref:System.Object.Equals%2A> 和 <xref:System.IComparable> 接口相关的各种规则的方法。  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## 示例  
 下面的应用程序测试上文所示的 <xref:System.IComparable> 实现的行为。  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## 请参阅  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [相等运算符](../Topic/Equality%20Operators.md)