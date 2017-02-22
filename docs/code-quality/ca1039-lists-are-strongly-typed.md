---
title: "CA1039：列表已强类型化 | Microsoft Docs"
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
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1039：列表已强类型化
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护类型实现了 <xref:System.Collections.IList?displayProperty=fullName>，但是没有为以下的一个或多个项提供强类型方法：  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## 规则说明  
 此规则要求 <xref:System.Collections.IList> 实现提供强类型成员，以使用户在使用该接口提供的功能时不必将参数强制转换成 <xref:System.Object?displayProperty=fullName> 类型。  <xref:System.Collections.IList> 接口由可以通过索引访问的对象集合实现。  该规则假定实现 <xref:System.Collections.IList> 的类型这样做以管理类型比 <xref:System.Object> 更强的实例的集合。  
  
 <xref:System.Collections.IList> 实现 <xref:System.Collections.ICollection?displayProperty=fullName> 和 <xref:System.Collections.IEnumerable?displayProperty=fullName> 接口。  如果实现 <xref:System.Collections.IList>，则必须为 <xref:System.Collections.ICollection> 提供必需的强类型成员。  如果集合中的对象扩展了 <xref:System.ValueType?displayProperty=fullName>，则您必须为 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 提供一个强类型成员，以避免由装箱造成的性能下降；当集合的对象为引用类型时，不需要提供强类型成员。  
  
 为了符合该规则，请使用 InterfaceName.InterfaceMemberName 格式的名称（如 <xref:System.Collections.IList.Add%2A>）来显式实现接口成员。  这些显式接口成员使用由该接口声明的数据类型。  使用接口成员名称（如 `Add`）来实现强类型成员。  将强类型成员声明为公共的，将参数和返回值声明为由集合管理的强类型。  这些强类型会替换由接口声明的较弱类型，例如 <xref:System.Object> 和 <xref:System.Array>。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请显式实现 <xref:System.Collections.IList> 成员，并为前面提到的成员提供强类型替代项。  有关正确实现 <xref:System.Collections.IList> 接口和提供所需的强类型成员的代码，请参见下面的示例。  
  
## 何时禁止显示警告  
 当实现新的基于对象的集合（如链接列表，其中扩展新集合的类型决定强类型）时，请禁止显示此规则发出的警告。  这些类型应当符合该规则并公开强类型成员。  
  
## 示例  
 在下面的示例中，如同所有强类型集合那样，类型 `YourType` 扩展了 <xref:System.Collections.CollectionBase?displayProperty=fullName>。  请注意，<xref:System.Collections.CollectionBase> 为您提供 <xref:System.Collections.IList> 接口的显式实现。  因此，您仅须为 <xref:System.Collections.IList> 和 <xref:System.Collections.ICollection> 提供强类型成员。  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## 相关规则  
 [CA1035：ICollection 实现含有强类型成员](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038：枚举数应强类型化](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## 请参阅  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>