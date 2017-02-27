---
title: "CA2241：为格式化方法提供正确的参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2241：为格式化方法提供正确的参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 传递到方法的 `format` 字符串参数，例如 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A> 或 <xref:System.String.Format%2A?displayProperty=fullName>，不包含对应于每个对象参数的格式项，反之亦然。  
  
## 规则说明  
 方法的参数，例如 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A> 和 <xref:System.String.Format%2A> 由一个格式字符串后接几个 <xref:System.Object?displayProperty=fullName> 实例组成。  格式字符串由文本和 {index\[,alignment\]\[:formatString\]} 形式的嵌入格式项组成。'index'是一个从零开始的整数，它指示要格式化的对象。  如果某对象在格式字符串中没有相应索引，该对象将被忽略。  如果“index”指定的对象不存在，将在运行时引发 <xref:System.FormatException?displayProperty=fullName>。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请为每个对象参数提供一个格式项，同时为每个格式项提供一个对象参数。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示与该规则冲突的两种情况。  
  
 [!CODE [FxCop.Usage.FormattingArguments#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments#1)]