---
title: "CA1717： 只有 FlagsAttribute 枚举应采用复数形式的名称 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 787b2f5c1a838bb6312fe5d08cd8328b07460243
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717：只有 FlagsAttribute 枚举应采用复数形式的名称
|||  
|-|-|  
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|  
|CheckId|CA1717|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 外部可见的枚举的名称以复数形式的单词和枚举未用标记<xref:System.FlagsAttribute?displayProperty=fullName>属性。  
  
## <a name="rule-description"></a>规则说明  
 命名约定规定，复数形式的枚举名称表示可以同时指定多个枚举值。 <xref:System.FlagsAttribute>告知编译器应将枚举视为位字段，它允许该枚举的按位运算。  
  
 如果仅一次，可以指定一个枚举值，则枚举的名称应为单数形式的单词。 例如，定义每周天数的枚举可能被用于在中使用应用程序可以在其中指定多天。 此枚举应具有<xref:System.FlagsAttribute>和可称为天。 允许仅指定一天的类似枚举将没有属性，并可能是称为 Day。  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这可减少所需了解新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员的时间。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 进行单数形式的单词的枚举名称或添加<xref:System.FlagsAttribute>。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果名称以单数形式的单词结尾。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1714：Flags 枚举应采用复数形式的名称](../code-quality/ca1714-flags-enums-should-have-plural-names.md)  
  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [枚举设计](/dotnet/standard/design-guidelines/enum)