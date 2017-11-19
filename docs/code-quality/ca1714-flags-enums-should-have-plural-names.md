---
title: "CA1714: Flags 枚举应采用复数形式的名称 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b83cb82dab5f723c656b51a5322df7d7aad4570c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714：Flags 枚举应采用复数形式的名称
|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共枚举具有<xref:System.FlagsAttribute?displayProperty=fullName>，并且其名称不结尾中。  
  
## <a name="rule-description"></a>规则说明  
 使用标记的类型<xref:System.FlagsAttribute>具有采用复数形式，因为该特性指明可以指定多个值的名称。 例如，定义每周天数的枚举可能被用于在中使用应用程序可以在其中指定多天。 此枚举应具有<xref:System.FlagsAttribute>和可称为天。 允许仅指定一天的类似枚举将没有属性，并可能是称为 Day。  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这减少了学习曲线，才能使用新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 复数形式的单词，请在枚举的名称，或删除<xref:System.FlagsAttribute>属性如果不应同时指定多个枚举值。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示冲突，如果名称为复数形式的单词，但不是以结尾的。 例如，如果以前所述在多个天枚举已命名 DaysOfTheWeek，这将违反规则，但不是其意图的逻辑。 此类冲突应禁止显示。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [枚举设计](/dotnet/standard/design-guidelines/enum)