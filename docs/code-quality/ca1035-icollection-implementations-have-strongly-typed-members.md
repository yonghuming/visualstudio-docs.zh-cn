---
title: "CA1035: ICollection 实现含有强类型成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6be0c08efcd1f409bfb69775822e4904372f2511
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035：ICollection 实现含有强类型成员
|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型实现<xref:System.Collections.ICollection?displayProperty=fullName>但不是提供强类型的方法<xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>。 强类型的版本<xref:System.Collections.ICollection.CopyTo%2A>必须接受两个参数，并且不能具有<xref:System.Array?displayProperty=fullName>或数组<xref:System.Object?displayProperty=fullName>作为其第一个参数。  
  
## <a name="rule-description"></a>规则说明  
 此规则要求<xref:System.Collections.ICollection>实现提供强类型化成员，以便用户不需要强制转换到的自变量<xref:System.Object>键入当用户界面中使用提供的功能时。 此规则假定该类型实现<xref:System.Collections.ICollection>执行，因此，若要管理集合的实例的类型属于强于<xref:System.Object>。  
  
 <xref:System.Collections.ICollection> 实现 <xref:System.Collections.IEnumerable?displayProperty=fullName> 接口。 如果集合中的对象扩展<xref:System.ValueType?displayProperty=fullName>，你必须提供强类型的成员的<xref:System.Collections.IEnumerable.GetEnumerator%2A>以避免由装箱造成的性能下降。 这不需要的对象集合的引用类型时。  
  
 若要实现接口成员的强类型的版本，实现接口成员显式窗体中使用名称`InterfaceName.InterfaceMemberName`，如<xref:System.Collections.ICollection.CopyTo%2A>。 显式接口成员的界面使用声明的数据类型。 通过使用接口成员的名称，如实现强类型的成员<xref:System.Collections.ICollection.CopyTo%2A>。 声明为公共的强类型的成员和声明的参数和返回值可由集合的强类型。 强类型替代较弱类型，如<xref:System.Object>和<xref:System.Array>由接口声明。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请显式实现接口成员 (将其声明为<xref:System.Collections.ICollection.CopyTo%2A>)。 添加公共的强类型的成员，并声明为`CopyTo`，并使其采用强类型化的数组作为其第一个参数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果你实现了基于对象的一个新集合，如二进制树中，其中扩展新集合的类型决定强类型，禁止显示此规则的警告。 这些类型应符合此规则，并公开强类型的成员。  
  
## <a name="example"></a>示例  
 下面的示例演示实现的正确方法<xref:System.Collections.ICollection>。  
  
 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1038：枚举数应强类型化](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039：列表已强类型化](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>