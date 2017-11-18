---
title: "CA1005： 避免泛型类型的参数过多 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b5fad132dfdda0ef12e6d74c503c5d27024a8382
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005：避免泛型类型的参数过多
|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 外部可见的泛型类型具有两个以上的类型参数。  
  
## <a name="rule-description"></a>规则说明  
 泛型类型包含的类型参数越多，越难以知道并记住每个类型参数各代表什么。 它是使用一个类型参数，如下所示通常明显`List<T>`，并在某些情况下有两个类型参数，如下所示`Dictionary<TKey, TValue>`。 如果存在两个以上的类型参数，都会感到过于困难适用于大多数用户 (例如，`TooManyTypeParameters<T, K, V>`在 C# 或`TooManyTypeParameters(Of T, K, V)`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更改为使用不能超过两个类型参数的设计。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 除非设计确实需要两个以上的类型参数不禁止显示此规则的警告。 提供易于了解和使用的语法中的泛型可以减少需要了解并增加新库采用率的时间。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1010：集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公开泛型列表](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006：不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法应提供类型形参](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：使用泛型事件处理程序实例](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007：在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>另请参阅  
 [泛型](/dotnet/csharp/programming-guide/generics/index)