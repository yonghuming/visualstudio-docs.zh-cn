---
title: "CA1018：用 AttributeUsageAttribute 标记特性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018：用 AttributeUsageAttribute 标记特性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> 特性不在自定义特性中。  
  
## 规则说明  
 当定义自定义特性时，用 <xref:System.AttributeUsageAttribute> 标记该特性，以指示源代码中可以应用自定义特性的位置。  特性的含义和预定用法将决定它在代码中的有效位置。  例如，可以定义一个特性，用于标识由谁来负责维护和增强库中的每种类型，并且始终在类型级别分配责任。  在这种情况下,编译器应该在类、枚举和接口上启用此特性，而不应在方法、事件或属性上启用它。  组织策略和过程将指示是否在程序集上允许该特性。  
  
 <xref:System.AttributeTargets?displayProperty=fullName> 枚举定义可以为自定义特性指定的目标。  如果省略 <xref:System.AttributeUsageAttribute>，自定义特性将对所有目标有效，如 <xref:System.AttributeTargets> 枚举的 `All` 值所定义的那样。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使用 <xref:System.AttributeUsageAttribute> 为特性指定目标。  请参见下面的示例。  
  
## 何时禁止显示警告  
 应当修复与该规则的冲突，而不应排除警告消息。  即使特性继承了 <xref:System.AttributeUsageAttribute>，为了简化代码维护，也应该显示该特性。  
  
## 示例  
 下面的示例定义了两个特性。  `BadCodeMaintainerAttribute` 错误地省略 <xref:System.AttributeUsageAttribute> 语句，而 `GoodCodeMaintainerAttribute` 正确地实现节前面所述的特性。  请注意，设计规则[CA1019：定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)需要属性 `DeveloperName`，为了保持完整性，包含了该属性。  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## 相关规则  
 [CA1019：定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813：避免使用未密封的特性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## 请参阅  
 [特性](../Topic/Attributes1.md)