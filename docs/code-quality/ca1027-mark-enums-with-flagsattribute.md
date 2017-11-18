---
title: "CA1027： 用 FlagsAttribute 标记枚举 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e2fa3e93b8c4673a4b50b1baa46befbc01f7f7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027：用 FlagsAttribute 标记枚举
|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 公共枚举的值为 2 的幂或是在枚举中定义其他值的组合和<xref:System.FlagsAttribute?displayProperty=fullName>属性不存在。 若要减少误报，此规则不会报告违反了为具有连续值的枚举。  
  
## <a name="rule-description"></a>规则说明  
 枚举是一种值类型，它定义一组相关的已命名常数。 应用<xref:System.FlagsAttribute>到已命名的常数可以有意义的方式组合一个枚举。 例如，考虑在应用程序，用于跟踪的哪一天的资源有星期几的枚举。 如果使用的枚举的已编码的每个资源的可用性<xref:System.FlagsAttribute>可以表示存在，几天的任何组合。 如果没有属性，可以表示仅一个日期是星期几。  
  
 对于存储 combinable 枚举的字段，单独的枚举值视为组字段中的位数。 因此，此类字段有时称为*位域*。 若要合并的位字段中存储的枚举值，使用布尔条件运算符。 若要测试的位字段，以确定是否存在特定的枚举值，请使用布尔逻辑运算符。 对于存储和检索正确组合的枚举值的位字段，枚举中定义的每个值必须是 2 的幂。 除非该条件，否则布尔逻辑运算符不能提取的字段中存储的单独的枚举值。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将添加<xref:System.FlagsAttribute>为枚举。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果您不希望可组合的枚举值，禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 在下面的示例中，`DaysEnumNeedsFlags`是一个枚举，满足的要求使用<xref:System.FlagsAttribute>，但不包含该列。 `ColorEnumShouldNotHaveFlag`枚举没有为 2 的两个，幂的值，但错误地指定<xref:System.FlagsAttribute>。 这违反了规则[CA2217： 不要不用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)。  
  
 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.FlagsAttribute?displayProperty=fullName>