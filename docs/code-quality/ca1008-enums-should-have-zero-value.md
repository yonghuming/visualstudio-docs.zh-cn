---
title: "CA1008： 枚举应具有零值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 84c43a95cd607a13a302e2247cacb091a39a3070
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008：枚举应具有零值
|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|类别|Microsoft.Design|  
|是否重大更改|无间断-当系统提示你添加**无**到非标志枚举的值。中断性-当系统提示要重命名或删除任何枚举值。|  
  
## <a name="cause"></a>原因  
 一个枚举，而无需应用<xref:System.FlagsAttribute?displayProperty=fullName>未定义的值为零; 或已应用的枚举的成员<xref:System.FlagsAttribute>定义了一个成员，其值为零但其名称不是 'None' 或枚举定义多个零值成员。  
  
## <a name="rule-description"></a>规则说明  
 未初始化枚举，就像其他值类型，默认值为零。 非标志特性的枚举应定义了值为零，因此，默认值是有效的值的枚举的成员。 如果适当，名称，该成员 None。 否则，将分配零到最常使用的成员。 请注意，默认情况下，是否第一个枚举成员的值未在声明中，设置其值为零。  
  
 如果具有一个枚举<xref:System.FlagsAttribute>应用定义零值的成员，其名称应为 None，以指示已在枚举中设置的任何值。 将任何其他用途违背使用零值的成员<xref:System.FlagsAttribute>在于 AND 和 OR 按位运算符对该成员无用。 这意味着应将该只有一个成员分配的值为零。 请注意，如果多个成员具有零值，则会在标志特性的枚举，`Enum.ToString()`返回不正确的结果不为零的成员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则，非标志特性的枚举的冲突，定义一个具有值为零; 的成员这是一项非重大更改。 对于带有标志属性的枚举定义值为零的成员，None 将此成员，然后删除具有值为零; 的任何其他成员这是一项重大更改。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不要禁止显示此规则对以前发布的标志特性化枚举除外的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示满足该规则的两个枚举和枚举， `BadTraceOptions`，违反了规则。  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700：不要命名“Reserved”枚举值](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712：不要将类型名用作枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028：枚举存储应为 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Enum?displayProperty=fullName>