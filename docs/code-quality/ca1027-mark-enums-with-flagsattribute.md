---
title: "CA1027：用 FlagsAttribute 标记枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1027：用 FlagsAttribute 标记枚举
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 公共枚举的值是 2 的幂或枚举中定义的其他值的组合，而且 <xref:System.FlagsAttribute?displayProperty=fullName> 特性不存在。  为减少误报，对于具有连续值的枚举，该规则不报告冲突。  
  
## 规则说明  
 枚举是一种值类型，它定义一组相关的已命名常数。  如果可以按照有意义的方式组合一个枚举的已命名常数，则对该枚举应用 <xref:System.FlagsAttribute>。  例如，在跟踪哪些日期资源可用的应用程序中，可考虑包含一周中各天的枚举。  如果在存在 <xref:System.FlagsAttribute> 的情况下使用枚举编码每个资源的可用性，则可以表示一周中任意几天的组合。  如果没有该特性，则只能表示每周中的一天。  
  
 对于存储可组合枚举的字段，将单独枚举值视为该字段中的位组。  所以，这类字段有时称为“位字段”。  要组合枚举值以存储在位字段中，请使用布尔条件运算符。  要测试位字段以确定是否存在特定枚举值，请使用布尔逻辑运算符。  要使位字段能够正确存储和检索组合枚举值，枚举中定义的每个值都必须是 2 的幂。  除非满足该条件，否则布尔逻辑运算符将无法提取该字段中存储的单独枚举值。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将 <xref:System.FlagsAttribute> 添加到枚举。  
  
## 何时禁止显示警告  
 如果您不希望枚举值可组合，请禁止显示此规则发出的警告。  
  
## 示例  
 在下面的示例中，`DaysEnumNeedsFlags` 是符合使用 <xref:System.FlagsAttribute> 的要求但不具有该属性的枚举。  `ColorEnumShouldNotHaveFlag` 枚举的值不是 2 的幂，但错误地指定了 <xref:System.FlagsAttribute>。  这违反了规则 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)。  
  
 [!CODE [FxCop.Design.EnumFlags#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags#1)]  
  
## 相关规则  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## 请参阅  
 <xref:System.FlagsAttribute?displayProperty=fullName>