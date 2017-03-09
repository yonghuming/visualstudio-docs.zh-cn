---
title: "CA1813：避免使用未密封的特性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813：避免使用未密封的特性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|类别|Microsoft.Performance|  
|是否重大更改|是|  
  
## 原因  
 继承自 <xref:System.Attribute?displayProperty=fullName> 的某公共类型不是抽象类型且未密封（在 Visual Basic 中为 `NotInheritable`）。  
  
## 规则说明  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类库提供用于检索自定义特性的方法。  默认情况下，这些方法搜索特性继承层次结构；例如，<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> 搜索指定的特性类型，或搜索任何扩展指定特性类型的特性类型。  通过密封特性，将无需搜索继承层次结构，且能够提高性能。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请密封特性类型或使其成为抽象类型。  
  
## 何时禁止显示警告  
 可以安全地禁止显示此规则发出的警告。  仅在定义特性层次结构且无法密封特性或使其成为抽象类型时，才应该执行该操作。  
  
## 示例  
 下面的示例演示满足该规则的自定义特性。  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## 相关规则  
 [CA1019：定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018：用 AttributeUsageAttribute 标记特性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## 请参阅  
 [特性](../Topic/Attributes1.md)