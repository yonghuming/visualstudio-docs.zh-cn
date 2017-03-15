---
title: "CA1007：在适用处使用泛型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1007：在适用处使用泛型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的方法包含类型为 <xref:System.Object?displayProperty=fullName> 的引用参数，而包含程序集以 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 为目标。  
  
## 规则说明  
 引用参数是用 `ref`（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `ByRef`）关键字修饰的参数。  为引用参数提供的参数类型必须与引用参数类型完全匹配。  若要使用从引用参数类型派生的类型，必须首先对该类型进行强制转换，然后将该类型分配给引用参数类型的变量。  使用泛型方法使受约束的所有类型都可以传递给方法，而无需先将类型强制转换为引用参数类型。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将方法变成泛型方法，并将 <xref:System.Object> 参数替换成类型参数。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示既作为非泛型方法实现也作为泛型方法实现的常规用途交换例程。  请注意与非泛型方法相比，使用泛型方法交换字符串的有效性。  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## 相关规则  
 [CA1005：避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公开泛型列表](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：使用泛型事件处理程序实例](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
## 请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)