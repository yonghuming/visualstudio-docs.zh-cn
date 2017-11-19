---
title: "CA1819： 属性不应返回数组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2bd2aae360789646c78fa6b292b1ad97490fc2da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819：属性不应返回数组
|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|类别|Microsoft.Performance|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共类型中的公共或受保护属性返回一个数组。  
  
## <a name="rule-description"></a>规则说明  
 数组由属性返回不写保护，即使属性是只读的。 若要使数组不会被更改，属性必须返回数组的副本。 通常，用户不能理解调用这种属性的负面性能影响。 具体而言，它们可以将属性用作索引属性。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，使方法的属性或更改要返回集合的属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 属性可以包含返回数组的属性，但不能包含返回集合的属性。 你可以禁止显示警告引发派生自的特性属性<xref:System.Attribute>类。 否则，不要禁止显示此规则的警告。  
  
## <a name="example-violation"></a>冲突的示例  
  
### <a name="description"></a>描述  
 下面的示例演示了违反此规则的属性。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### <a name="comments"></a>注释  
 若要修复与此规则的冲突，使方法的属性或更改属性，以返回而不是数组的集合。  
  
## <a name="change-the-property-to-a-method-example"></a>将属性更改为方法示例  
  
### <a name="description"></a>描述  
 下面的示例通过将属性更改为方法中修复了冲突。  
  
### <a name="code"></a>代码  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## <a name="return-a-collection-example"></a>返回集合的示例。  
  
### <a name="description"></a>描述  
 下面的示例通过将属性更改为返回修复了冲突  
  
 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## <a name="allowing-users-to-modify-a-property"></a>允许用户修改属性  
  
### <a name="description"></a>描述  
 你可能想要允许的类的使用者修改属性。 下面的示例演示了违反此规则的读/写属性。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### <a name="comments"></a>注释  
 下面的示例通过将属性更改为返回修复了冲突<xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>。  
  
### <a name="code"></a>代码  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1024：在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)