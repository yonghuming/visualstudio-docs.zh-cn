---
title: "CA1714：Flags 枚举应采用复数形式的名称 | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714：Flags 枚举应采用复数形式的名称
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 公共枚举具有 <xref:System.FlagsAttribute?displayProperty=fullName> 并且其名称不是以“s”结尾。  
  
## 规则说明  
 标有 <xref:System.FlagsAttribute> 的类型具有复数形式的名称，因为该特性指明可以指定多个值。  例如，定义星期几的枚举可能打算在可以指定多天的应用程序中使用。  此枚举应具有 <xref:System.FlagsAttribute> 并且可称为“Days”。  只允许指定一天的类似枚举将没有该特性，并可称为“Day”。  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 使用复数形式的单词作为枚举的名称，或者，如果不应同时指定多个枚举值，则移除 <xref:System.FlagsAttribute> 特性。  
  
## 何时禁止显示警告  
 如果名称为复数形式的单词但不以“s”结尾，可以安全地禁止显示冲突。  例如，如果前面描述的多天枚举被命名为“DaysOfTheWeek”，这将与该规则的逻辑发生冲突，但与该规则的目的不冲突。  应禁止显示此类冲突。  
  
## 相关规则  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## 请参阅  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [枚举设计](../Topic/Enum%20Design.md)