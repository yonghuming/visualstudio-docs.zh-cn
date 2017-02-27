---
title: "CA1006：不要将泛型类型嵌套在成员签名中 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1006：不要将泛型类型嵌套在成员签名中
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的成员有包含嵌套类型参数的签名。  
  
## 规则说明  
 嵌套类型参数是一个类型参数，也是一个泛型类型。  若要调用签名包含嵌套类型参数的成员，用户必须实例化一个泛型类型，并将此类型传递到另一个泛型类型的构造函数。  所需的过程和语法很复杂，应当避免。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请更改设计，移除嵌套类型参数。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  按照容易理解和使用的语法提供泛型，不仅可以缩短学习新库所需的时间，而且还可以提高新库的使用率。  
  
## 示例  
 下面的示例演示了一个与该规则冲突的方法和调用该冲突方法所需的语法。  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## 相关规则  
 [CA1005：避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公开泛型列表](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1004：泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：使用泛型事件处理程序实例](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)