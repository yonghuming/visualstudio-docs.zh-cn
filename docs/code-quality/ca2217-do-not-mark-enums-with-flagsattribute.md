---
title: "CA2217：不要使用 FlagsAttribute 标记枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotMarkEnumsWithFlags"
  - "CA2217"
helpviewer_keywords: 
  - "CA2217"
  - "DoNotMarkEnumsWithFlags"
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2217：不要使用 FlagsAttribute 标记枚举
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 在外部可见的枚举使用 <xref:System.FlagsAttribute> 标记，并且它包含的一个或多个值不是 2 的幂或该枚举中其他定义的值的组合。  
  
## 规则说明  
 只有当枚举中定义的每一个值是 2 的幂或所定义值的组合时，该枚举才可以显示 <xref:System.FlagsAttribute> 属性。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请从枚举中移除 <xref:System.FlagsAttribute>。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例显示了枚举 Color，该枚举包含值 3，该值既不是 2 的幂，也不是任何定义的值的组合。  不应使用 <xref:System.FlagsAttribute> 标记 Color 枚举。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## 示例  
 下面的示例显示了枚举 Days，该枚举符合用 System.FlagsAttribute 标记的要求。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## 相关规则  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## 请参阅  
 <xref:System.FlagsAttribute?displayProperty=fullName>