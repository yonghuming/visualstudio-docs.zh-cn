---
title: "CA1813： 避免使用未密封的特性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5aec235494b29a21eb5a3c2de39a6933e04b0ebe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813：避免使用未密封的特性
|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|类别|Microsoft.Performance|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共类型都继承自<xref:System.Attribute?displayProperty=fullName>、 不是抽象的和未密封 (`NotInheritable`在 Visual Basic 中)。  
  
## <a name="rule-description"></a>规则说明  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类库提供用于检索自定义特性的方法。 默认情况下，这些方法搜索特性继承层次结构;例如<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>搜索指定的属性类型或任何扩展的指定的属性类型的属性类型。 密封特性，无需搜索继承层次结构中，且可以提高性能。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，密封属性类型，或使其成为抽象。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告。 仅当定义了属性层次结构和不能密封属性或使其成为抽象时，应执行此操作。  
  
## <a name="example"></a>示例  
 下面的示例演示满足此规则的自定义特性。  
  
 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1019：定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018：用 AttributeUsageAttribute 标记特性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 [特性](/dotnet/standard/design-guidelines/attributes)