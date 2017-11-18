---
title: "CA1018： 用 AttributeUsageAttribute 标记的属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9218d3908872871ff5dab13529e8b1cbcec0c8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018：用 AttributeUsageAttribute 标记特性
|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>属性上不存在自定义属性。  
  
## <a name="rule-description"></a>规则说明  
 当你定义的自定义特性时，则将其标记使用<xref:System.AttributeUsageAttribute>以指示源代码中可以应用自定义特性的位置。 特性的含义和预定用法将决定它在代码中的有效位置。 例如，你可以定义该属性标识由谁来负责维护并增强在库中，每个类型和类型级别始终分配责任的人员。 在这种情况下，编译器应启用的属性类、 枚举和接口，但不是应允许它在方法、 事件或属性。 组织策略和过程将指示是否应在程序集上启用该属性。  
  
 <xref:System.AttributeTargets?displayProperty=fullName>枚举定义可以为自定义特性指定的目标。 如果省略<xref:System.AttributeUsageAttribute>，按照定义，进行有效的所有目标，自定义特性`All`值<xref:System.AttributeTargets>枚举。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 要修复与此规则的冲突，通过使用指定的属性的目标<xref:System.AttributeUsageAttribute>。 请参见以下示例。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 您应修复而排除警告消息的不是此规则的冲突。 即使属性继承<xref:System.AttributeUsageAttribute>，属性应为来简化代码维护。  
  
## <a name="example"></a>示例  
 下面的示例定义两个属性。 `BadCodeMaintainerAttribute`错误地省略<xref:System.AttributeUsageAttribute>语句，和`GoodCodeMaintainerAttribute`正确地实现此部分中前面描述的属性。 请注意，属性`DeveloperName`所需的设计规则[CA1019： 定义特性自变量的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)，并且将包含出于完整性的考虑。  
  
 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1019：定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813：避免使用未密封的特性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>另请参阅  
 [特性](/dotnet/standard/design-guidelines/attributes)