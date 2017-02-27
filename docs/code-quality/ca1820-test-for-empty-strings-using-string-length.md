---
title: "CA1820：使用字符串长度测试是否有空字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1820：使用字符串长度测试是否有空字符串
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 将字符串与空字符串比较时使用的是 <xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
## 规则说明  
 使用 <xref:System.String.Length%2A?displayProperty=fullName> 属性或 <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> 方法比较字符串要比使用 <xref:System.Object.Equals%2A> 的速度快得多。  这是因为与 <xref:System.String.IsNullOrEmpty%2A> 或者为检索 <xref:System.String.Length%2A> 属性值并将其与零比较所需执行的指令数相比，<xref:System.Object.Equals%2A> 执行更多的 MSIL 指令。  
  
 您应该注意，<xref:System.Object.Equals%2A> 和 <xref:System.String.Length%2A> \=\= 0 对于空字符串的行为表现不同。  如果您尝试获取空字符串的 <xref:System.String.Length%2A> 属性的值，公共语言运行时将引发 <xref:System.NullReferenceException?displayProperty=fullName>。  如果比较空 \(null\) 字符串和空 \(empty\) 字符串，则公共语言运行时不会引发异常；比较将返回 `false`。  对空字符串进行测试不会显著影响这两种方法的相对性能。  当目标为 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 时，使用 <xref:System.String.IsNullOrEmpty%2A> 方法。  否则，在可能的情况下请使用 <xref:System.String.Length%2A> \=\= 比较。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将比较方法更改为使用 <xref:System.String.Length%2A> 属性测试空字符串。  如果目标为 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，则使用 <xref:System.String.IsNullOrEmpty%2A> 方法。  
  
## 何时禁止显示警告  
 如果不用考虑性能问题，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示用于查找空字符串的不同技术。  
  
 [!CODE [FxCop.Performance.StringTest#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest#1)]