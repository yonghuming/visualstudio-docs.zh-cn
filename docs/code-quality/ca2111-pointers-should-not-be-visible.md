---
title: "CA2111：指针应为不可见 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2111：指针应为不可见
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护的 <xref:System.IntPtr?displayProperty=fullName> 或 <xref:System.UIntPtr?displayProperty=fullName> 字段不是只读的。  
  
## 规则说明  
 <xref:System.IntPtr> 和 <xref:System.UIntPtr> 是用于访问非托管内存的指针类型。  如果指针不是私有、内部或只读的，则恶意代码可以更改指针的值，这样，便有可能允许访问内存中的任意位置或导致应用程序或系统失败。  
  
 如果希望保护对包含指针字段的类型的访问，请参见 [CA2112：受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。  
  
## 如何解决冲突  
 通过使指针成为只读、内部或私有指针，来保护指针。  
  
## 何时禁止显示警告  
 如果不依赖指针的值，则可以禁止显示此规则发出的警告。  
  
## 示例  
 下面的代码演示与规则冲突的指针和满足规则的指针。  注意，非私有指针也与规则[CA1051：不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)冲突。  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## 相关规则  
 [CA2112：受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051：不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## 请参阅  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>