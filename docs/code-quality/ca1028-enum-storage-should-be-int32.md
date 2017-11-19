---
title: "CA1028： 枚举存储应为 Int32 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd0f74a322e136263b6445db2692380dfea2efa3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028：枚举存储应为 Int32
|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共枚举的基础类型不是<xref:System.Int32?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 枚举是一种值类型，它定义一组相关的已命名常数。 默认情况下，<xref:System.Int32?displayProperty=fullName>数据类型用于存储常量值。 即使您可以更改此基础类型，它是不必要或建议在大多数情况下。 请注意，通过使用小于数据类型实现没有显著的性能提升<xref:System.Int32>。 如果无法使用默认数据类型，则应使用一个公共语言系统 (CLS) 的符合整型<xref:System.Byte>， <xref:System.Int16>， <xref:System.Int32>，或<xref:System.Int64>若要确保枚举的所有值可以都表示的符合 CLS 的编程语言。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，除非存在大小或兼容性问题，请使用<xref:System.Int32>。 对于情况其中<xref:System.Int32>足够大，无法保存的值，请使用<xref:System.Int64>。 如果向后兼容性要求将较小的数据类型，使用<xref:System.Byte>或<xref:System.Int16>。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 只有当向后兼容性问题需要它，禁止显示此规则的警告。 在应用程序，不符合此规则通常不会导致问题。 在库中，其中语言互操作性是必需的不符合此规则可能产生不良影响你的用户。  
  
## <a name="example-of-a-violation"></a>冲突的示例  
  
### <a name="description"></a>描述  
 下面的示例演示两个不使用建议的基础数据类型的枚举。  
  
### <a name="code"></a>代码  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>修复方法的示例  
  
### <a name="description"></a>描述  
 下面的示例通过更改基础数据类型设置为修复前面的冲突<xref:System.Int32>。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1008：枚举应具有零值](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700：不要命名“Reserved”枚举值](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712：不要将类型名用作枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>