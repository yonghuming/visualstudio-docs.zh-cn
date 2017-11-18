---
title: "CA1003： 使用泛型事件处理程序实例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf4f11f3f8fae1130c2cc99468a40ed269c77481
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003：使用泛型事件处理程序实例
|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|CheckId|CA1003|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 包含的类型的委托返回 void，该签名包含两个参数 （一个对象的第一个和第二个是可以分配给 EventArgs 的类型） 和包含程序集针对[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]。  
  
## <a name="rule-description"></a>规则说明  
 之前[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，以便将自定义信息传递给事件处理程序，新的委托，必须指定派生自的类声明<xref:System.EventArgs?displayProperty=fullName>类。 这已不再是实际中[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，后者引入<xref:System.EventHandler%601?displayProperty=fullName>委托。 此泛型委托允许的任何类都派生自<xref:System.EventArgs>与事件处理程序一起使用。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 要修复与此规则的冲突，移除了该委托，并通过使用取代其用途<xref:System.EventHandler%601?displayProperty=fullName>委托。 如果该委托是通过自动生成[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]编译器，更改用于事件声明中的语法<xref:System.EventHandler%601?displayProperty=fullName>委托。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例显示一个与该规则冲突的委托。 在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]示例中，注释说明了如何修改以满足该规则的示例。 对于 C# 示例，后面的示例演示修改后的代码。  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## <a name="example"></a>示例  
 下面的示例从前面的示例，其中满足该规则，并替换在中的使用它删除与委托声明`ClassThatRaisesEvent`和`ClassThatHandlesEvent`方法通过使用<xref:System.EventHandler%601?displayProperty=fullName>委托。  
  
 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1005：避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公开泛型列表](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006：不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法应提供类型形参](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007：在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>另请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)