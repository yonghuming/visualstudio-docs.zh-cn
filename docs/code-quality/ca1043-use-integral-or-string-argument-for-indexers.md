---
title: "CA1043：将整型或字符串参数用于索引器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1043：将整型或字符串参数用于索引器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护类型包含使用 <xref:System.Int32?displayProperty=fullName>、<xref:System.Int64?displayProperty=fullName>、<xref:System.Object?displayProperty=fullName> 或 <xref:System.String?displayProperty=fullName> 以外的索引类型的公共或受保护索引器。  
  
## 规则说明  
 索引器（即索引属性），应将整型或字符串类型用于索引。  这些类型一般用于为数据结构创建索引和提高库的可用性。  <xref:System.Object> 类型的使用应仅限于不能在设计时指定特定整型或字符串类型的那些情况。  如果设计需要对索引使用其他类型，请重新考虑该类型是否代表逻辑数据存储区。  如果该类型不代表逻辑数据存储区，请使用方法。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将索引更改为整型或字符串类型，或者使用方法代替索引器。  
  
## 何时禁止显示警告  
 仅在认真考虑非标准索引器的需要后，再禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示使用 <xref:System.Int32> 索引的索引器。  
  
 [!CODE [FxCop.Design.IntegralOrStringIndexers#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers#1)]  
  
## 相关规则  
 [CA1023：索引器不应是多维的](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024：在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)