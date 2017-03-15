---
title: "CA1057：字符串 URI 重载调用 System.Uri 重载 | Microsoft Docs"
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
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057：字符串 URI 重载调用 System.Uri 重载
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 某类型声明了仅在使用 <xref:System.Uri?displayProperty=fullName> 参数替换字符串参数方面不同的方法重载，且采用字符串参数的重载不调用采用 <xref:System.Uri> 参数的重载。  
  
## 规则说明  
 由于各个重载仅字符串\/<xref:System.Uri> 参数不同，所以假设该字符串代表统一资源标识符 \(URI\)。  URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。  <xref:System.Uri> 类以一种安全的方式提供这些服务。  要获得 <xref:System.Uri> 类的好处，字符串重载应使用字符串参数调用 <xref:System.Uri> 重载。  
  
## 如何解决冲突  
 重新实现使用 URI 的字符串表示形式的方法，使其能够使用字符串变量创建 <xref:System.Uri> 类的实例，然后将 <xref:System.Uri> 对象传递给具有 <xref:System.Uri> 参数的重载。  
  
## 何时禁止显示警告  
 如果字符串参数不表示 URI，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个正确实现的字符串重载。  
  
 [!CODE [FxCop.Design.CallUriOverload#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload#1)]  
  
## 相关规则  
 [CA2234：传递 System.Uri 对象，而不传递字符串](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1056：URI 属性不应是字符串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054：URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055：URI 返回值不应是字符串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)