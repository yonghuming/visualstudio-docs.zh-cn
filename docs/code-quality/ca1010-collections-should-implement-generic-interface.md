---
title: "CA1010：集合应实现泛型接口 | Microsoft Docs"
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
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1010：集合应实现泛型接口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 某个外部可见的类型实现 <xref:System.Collections.IEnumerable?displayProperty=fullName> 接口，但不实现 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 接口，而包含程序集以 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 为目标。  此规则忽略实现 <xref:System.Collections.IDictionary?displayProperty=fullName> 的类型。  
  
## 规则说明  
 若要扩大集合的用途，应实现某个泛型集合接口。  然后，可以使用该集合来填充泛型集合类型，例如：  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请实现下列泛型集合接口之一：  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## 何时禁止显示警告  
 可以安全地禁止显示与该规则有关的警告；但是，集合在使用上将有更多的限制。  
  
## 冲突的示例  
  
### 说明  
 下面的示例演示一个从非泛型 `CollectionBase` 类派生的类（引用类型），它与此规则冲突。  
  
### 代码  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### 注释  
 若要修复与此规则的冲突，应该实现泛型接口或将基类更改为已经实现泛型和非泛型接口的类型，例如 `Collection<T>` 类。  
  
## 通过基类更改进行修复  
  
### 说明  
 下面的示例通过将集合的基类从非泛型 `CollectionBase` 类更改为泛型 `Collection<T>`（[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Collection(Of T)`）类来修复冲突。  
  
### 代码  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### 注释  
 更改已发布类的基类视为对现有使用者进行了重大更改。  
  
## 通过接口实现进行修复  
  
### 说明  
 下面的示例通过实现以下泛型接口来修复冲突：`IEnumerable<T>`、`ICollection<T>` 和 `IList<T>`（[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `IEnumerable(Of T)`、`ICollection(Of T)` 和 `IList(Of T)`）。  
  
### 代码  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## 相关规则  
 [CA1005：避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000：不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公开泛型列表](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：使用泛型事件处理程序实例](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)