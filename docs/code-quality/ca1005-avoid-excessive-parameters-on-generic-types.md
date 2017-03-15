---
title: "CA1005：避免泛型类型的参数过多 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1005：避免泛型类型的参数过多
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的泛型类型具有两个以上的类型参数。  
  
## 规则说明  
 泛型类型包含的类型参数越多，越难以知道并记住每个类型参数各代表什么。  包含一个类型参数通常很显然，如在 `List<T>` 中，在某些情况下包含两个类型参数也很显然，如在 `Dictionary<TKey, TValue>` 中。  但是，如果存在两个以上的类型参数，则大多数用户都会感到过于困难（例如，C\# 中的 `TooManyTypeParameters<T, K, V>` 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `TooManyTypeParameters(Of T, K, V)`）。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请更改设计以确保使用的类型参数不超过两个。  
  
## 何时禁止显示警告  
 除非设计确实需要两个以上的类型参数，否则不要禁止显示此规则发出的警告。  按照容易理解和使用的语法提供泛型，不仅可以缩短学习新库所需的时间，而且还可以提高新库的使用率。  
  
## 相关规则  
 [CA1010：集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公开泛型列表](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：使用泛型事件处理程序实例](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)