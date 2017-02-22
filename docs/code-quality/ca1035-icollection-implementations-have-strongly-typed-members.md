---
title: "CA1035：ICollection 实现含有强类型成员 | Microsoft Docs"
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
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1035：ICollection 实现含有强类型成员
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 某公共类型或受保护类型实现 <xref:System.Collections.ICollection?displayProperty=fullName>，但没有提供 <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> 的强类型方法。  <xref:System.Collections.ICollection.CopyTo%2A> 的强类型版本必须接受两个参数，并且不能使用 <xref:System.Array?displayProperty=fullName> 或 <xref:System.Object?displayProperty=fullName> 的数组作为第一个参数。  
  
## 规则说明  
 此规则要求 <xref:System.Collections.ICollection> 实现提供强类型成员，以使用户在使用该接口提供的功能时不必将参数强制转换成 <xref:System.Object> 类型。  该规则假定实现 <xref:System.Collections.ICollection> 的类型执行此操作来管理强于 <xref:System.Object> 的类型的实例集合。  
  
 <xref:System.Collections.ICollection> 实现 <xref:System.Collections.IEnumerable?displayProperty=fullName> 接口。  如果集合中的对象扩展了 <xref:System.ValueType?displayProperty=fullName>，则您必须为 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 提供一个强类型成员，以避免由装箱造成的性能下降。  当集合的对象是引用类型时，这是不需要的。  
  
 要实现接口成员的强类型版本，请使用 `InterfaceName.InterfaceMemberName` 形式的名称（如 <xref:System.Collections.ICollection.CopyTo%2A>）来显式实现接口成员。  这些显式接口成员使用由该接口声明的数据类型。  使用接口成员名称（如 <xref:System.Collections.ICollection.CopyTo%2A>）来实现强类型成员。  将强类型成员声明为公共的，将参数和返回值声明为由集合管理的强类型。  这些强类型会替换由接口声明的较弱类型，例如 <xref:System.Object> 和 <xref:System.Array>。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请显式实现接口成员（将其声明为 <xref:System.Collections.ICollection.CopyTo%2A>）。  添加被声明为 `CopyTo` 的公共强类型成员，使该成员采用强类型数组作为它的第一个参数。  
  
## 何时禁止显示警告  
 在实现基于新对象的集合（如扩展新集合的类型确定强类型的二叉树）时，可以禁止显示此规则发出的警告。  这些类型应当符合该规则并公开强类型成员。  
  
## 示例  
 下面的示例演示实现 <xref:System.Collections.ICollection> 的正确方法。  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## 相关规则  
 [CA1038：枚举数应强类型化](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039：列表已强类型化](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## 请参阅  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>