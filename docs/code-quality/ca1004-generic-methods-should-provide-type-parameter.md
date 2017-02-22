---
title: "CA1004：泛型方法应提供类型参数 | Microsoft Docs"
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
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1004：泛型方法应提供类型参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的泛型方法的参数签名不包含与该方法的所有类型参数对应的类型。  
  
## 规则说明  
 推理是指由传递给泛型方法的参数的类型来确定该方法的类型参数，而不是显式指定类型参数。  若要启用推理，泛型方法的参数签名必须包含与该方法的类型参数属于相同类型的参数。  在这种情况下，不必指定类型参数。  对所有类型参数都使用推理时，调用泛型实例方法和非泛型实例方法的语法完全相同。  这样可简化泛型方法的使用。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请更改设计以使参数签名包含对于该方法的每个类型参数而言都完全相同的类型。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  按照容易理解和使用的语法提供泛型，不仅可以缩短学习新库所需的时间，而且还可以提高新库的使用率。  
  
## 示例  
 下面的示例演示了调用两个泛型方法的语法。  `InferredTypeArgument` 的类型参数是推断出来的，而 `NotInferredTypeArgument` 的类型参数则必须是显式指定的。  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## 相关规则  
 [CA1005：避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公开泛型列表](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003：使用泛型事件处理程序实例](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)