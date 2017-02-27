---
title: "CA1000：不要在泛型类型中声明静态成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1000：不要在泛型类型中声明静态成员
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的泛型类型包含 `static`（在 Visual Basic 中为 `Shared`）成员。  
  
## 规则说明  
 调用泛型类型的 `static` 成员时，必须指定该类型的类型参数。  当调用不支持推理的泛型实例成员时，必须指定该成员的类型参数。  在上述两种情况下，指定类型参数的语法有所不同且易于混淆，下面的调用说明了这一点：  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 通常，前面的两种声明均应避免，以便在调用成员时不必指定类型参数。  这样，调用泛型中的成员所用的语法与调用非泛型中的成员所用的语法别无二致。  有关更多信息，请参见 [CA1004：泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请移除静态成员或将它更改为实例成员。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  按照容易理解和使用的语法提供泛型，不仅可以缩短学习新库所需的时间，而且还可以提高新库的使用率。  
  
## 相关规则  
 [CA1005：避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002：不要公开泛型列表](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：使用泛型事件处理程序实例](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)