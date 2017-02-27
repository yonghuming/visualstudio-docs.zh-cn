---
title: "CA2140：透明代码不得引用安全关键项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2140：透明代码不得引用安全关键项
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 透明方法：  
  
-   处理安全关键安全异常类型  
  
-   拥有标记为安全关键类型的参数  
  
-   拥有带安全关键约束的参数  
  
-   拥有安全关键类型的局部变量  
  
-   引用标记为关键安全类型或成员的类型  
  
-   调用标记为“安全关键”的方法  
  
-   引用标记为关键安全类型或成员的字段  
  
-   返回标记为关键安全类型或成员的类型  
  
## 规则说明  
 用 <xref:System.Security.SecurityCriticalAttribute> 特性标记的代码都是安全关键代码。  透明方法不能使用安全关键元素。  如果透明类型尝试使用安全关键类型，则会引发 <xref:System.TypeAccessException>, <xref:System.MethodAccessException> 或 <xref:System.FieldAccessException>。  
  
## 如何解决冲突  
 要解决此规则的冲突，进行以下操作之一：  
  
-   用 <xref:System.Security.SecurityCriticalAttribute> 特性标记的安全关键代码标记代码元素。  
  
     \- 或 \-  
  
-   从标记为关键安全类型或成员的代码元素中删除 <xref:System.Security.SecurityCriticalAttribute> 特性，并使用 <xref:System.Security.SecuritySafeCriticalAttribute> 或 <xref:System.Security.SecurityTransparentAttribute> 特性标记它们。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 在下面的示例中，透明的方法尝试引用安全关键泛型集合、安全关键字段和安全的关键方法。  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## 请参阅  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>