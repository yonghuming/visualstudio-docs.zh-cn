---
title: "CA1051： 不要声明可见实例字段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c80ac321100ecc0f88811332c73bdfd99b5a6a99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051：不要声明可见实例字段
|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 外部可见的类型具有一个外部可见实例字段。  
  
## <a name="rule-description"></a>规则说明  
 字段的主要用途应是作为实现的详细信息。 字段应为`private`或`internal`并应通过使用属性公开。 它是很容易就能访问的字段，以及随着类型的特性的扩展，而不会引入的重大更改，可以更改的属性访问器中的代码访问的属性。 仅返回一个私有或内部字段的值的属性了优化，可与相媲美访问字段; 执行很少的性能提升属性的高于外部可见的字段的用法与相关联。  
  
 外部可见指`public`， `protected`，和`protected internal`(`Public`， `Protected`，和`Protected Friend`在 Visual Basic 中) 可访问性级别。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请字段`private`或`internal`和公开使用外部可见的属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 外部可见的字段不提供任何权益，这是对属性不可用。 此外，无法保护公共字段[链接需求](/dotnet/framework/misc/link-demands)。 请参阅[CA2112： 受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型 (`BadPublicInstanceFields`) 了违反此规则。 `GoodPublicInstanceFields`显示已纠正的代码。  
  
 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2112：受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## <a name="see-also"></a>另请参阅  
 [链接需求](/dotnet/framework/misc/link-demands)