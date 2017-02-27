---
title: "CA2243：应正确分析特性字符串文本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2243：应正确分析特性字符串文本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 特性的字符串文本参数不能正确解析为 URL、GUID 或版本。  
  
## 规则说明  
 因为特性是从 <xref:System.Attribute?displayProperty=fullName> 派生的，并且在编译时使用特性，所以只能向它们的构造函数传递常量值。  必须表示 URL、GUID 和版本的特性参数不能类型化为 <xref:System.Uri?displayProperty=fullName>、<xref:System.Guid?displayProperty=fullName> 和 <xref:System.Version?displayProperty=fullName>，因为这些类型不能表示为常量。  相反，它们必须用字符串表示。  
  
 因为参数的类型为字符串，所以可能会在编译时传递格式不正确的参数。  
  
 此规则使用命名试探查找表示统一资源标识符 \(URI\)、全局唯一标识符 \(GUID\) 或版本的参数，并验证传递的值是否正确。  
  
## 如何解决冲突  
 将参数字符串更改为格式正确的 URL、GUID 或版本。  
  
## 何时禁止显示警告  
 如果参数不表示 URI、GUID 或版本，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示与此规则冲突的 AssemblyFileVersionAttribute 的代码。  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 此规则由下列对象触发：  
  
-   包含“version”但不能解析为 System.Version 的参数。  
  
-   包含“guid”但不能解析为 System.Guid 的参数。  
  
-   包含“uri”、“urn”或“url”但不能解析为 System.Uri 的参数。  
  
## 请参阅  
 [CA1054：URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)