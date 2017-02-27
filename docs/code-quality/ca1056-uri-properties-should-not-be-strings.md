---
title: "CA1056：URI 属性不应是字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UriPropertiesShouldNotBeStrings"
  - "CA1056"
helpviewer_keywords: 
  - "CA1056"
  - "UriPropertiesShouldNotBeStrings"
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1056：URI 属性不应是字符串
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 某类型声明的字符串属性的名称包含“uri”、“Uri”、“urn”、“Urn”、“url”或“Url”。  
  
## 规则说明  
 该规则根据 Pascal 大小写约定将属性名称拆分为多个标记，然后检查每个标记是否与“uri”、“Uri”、“urn”、“Urn”、“url”或“Url”相等。  如果存在匹配项，则该规则假定属性表示统一资源标识符 \(URI\)。  URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。  <xref:System.Uri?displayProperty=fullName> 类以一种安全的方式提供这些服务。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将属性更改为 <xref:System.Uri> 类型。  
  
## 何时禁止显示警告  
 如果属性不表示 URI，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示与该规则冲突的 `ErrorProne` 类型和满足该规则的 `SaferWay` 类型。  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## 相关规则  
 [CA1054：URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055：URI 返回值不应是字符串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234：传递 System.Uri 对象，而不传递字符串](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057：字符串 URI 重载调用 System.Uri 重载](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)