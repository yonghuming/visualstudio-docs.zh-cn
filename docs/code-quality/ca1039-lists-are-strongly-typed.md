---
title: "CA1039： 列表已强类型化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 57bbb053c39680d8064fb757679ffadb3c87aeeb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039：列表已强类型化
|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型实现<xref:System.Collections.IList?displayProperty=fullName>但未提供的一个或多个以下的强类型化的方法：  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## <a name="rule-description"></a>规则说明  
 此规则要求<xref:System.Collections.IList>实现提供强类型化成员，以便用户不需要强制转换到的自变量<xref:System.Object?displayProperty=fullName>键入当用户界面中使用提供的功能时。 <xref:System.Collections.IList>接口由可按照索引访问的对象的集合。 此规则假定该类型实现<xref:System.Collections.IList>这样做是为了管理集合的实例的类型属于强于<xref:System.Object>。  
  
 <xref:System.Collections.IList>实现<xref:System.Collections.ICollection?displayProperty=fullName>和<xref:System.Collections.IEnumerable?displayProperty=fullName>接口。 如果你实现<xref:System.Collections.IList>，你必须提供必需的强类型的成员<xref:System.Collections.ICollection>。 如果集合中的对象扩展<xref:System.ValueType?displayProperty=fullName>，你必须提供强类型的成员的<xref:System.Collections.IEnumerable.GetEnumerator%2A>以避免导致性能降低由装箱导致; 这不是必需的对象集合的引用类型时。  
  
 若要符合此规则，实现接口成员显式使用名称的形式 InterfaceName.InterfaceMemberName，类似于<xref:System.Collections.IList.Add%2A>。 显式接口成员的界面使用声明的数据类型。 通过使用接口成员的名称，如实现强类型的成员`Add`。 声明为公共的强类型的成员和声明的参数和返回值可由集合的强类型。 强类型替代较弱类型，如<xref:System.Object>和<xref:System.Array>由接口声明。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，显式实现<xref:System.Collections.IList>成员和前面所述的成员提供强类型替代项。 正确实现的代码<xref:System.Collections.IList>接口，并提供所需强类型的成员，请参阅下面的示例。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 实现基于对象的一个新集合，如链接列表，其中扩展新集合的类型决定强类型时，禁止显示此规则的警告。 这些类型应符合此规则，并公开强类型的成员。  
  
## <a name="example"></a>示例  
 在下面的示例中，类型`YourType`扩展<xref:System.Collections.CollectionBase?displayProperty=fullName>，所有强类型的集合也应如此。 请注意，<xref:System.Collections.CollectionBase>提供的显式实现<xref:System.Collections.IList>接口供你。 因此，你必须只提供的强类型的成员<xref:System.Collections.IList>和<xref:System.Collections.ICollection>。  
  
 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1035：ICollection 实现含有强类型成员](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038：枚举数应强类型化](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>