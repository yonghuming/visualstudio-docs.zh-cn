---
title: "CA2112：受保护的类型不应公开字段 | Microsoft Docs"
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
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112：受保护的类型不应公开字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 某公共类型或受保护类型包含公共字段并且受 [链接需求](../Topic/Link%20Demands.md) 保护。  
  
## 规则说明  
 如果代码可以访问受链接要求保护的类型的实例，则该代码不必满足此链接要求就可以访问该类型的字段。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使字段成为非公共的并添加返回字段数据的公共属性或方法。  对类型的 LinkDemand 安全检查保护对类型的属性和方法的访问。  但是，代码访问安全不适用于字段。  
  
## 何时禁止显示警告  
 为解决安全问题并获得良好的设计，您都应该通过使公共字段成为非公共字段来修复冲突。  如果字段不保存应保持安全的信息并且您不依赖于该字段的内容，则可以禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例包含一个带有非安全字段的库类型 \(`SecuredTypeWithFields`\)，一个可以创建库类型实例但错误地将实例传递给没有权限创建这些实例的类型的类型 \(`Distributor`\)，以及可以读取实例字段的应用程序代码（即使没有保护类型安全的权限）。  
  
 下面的库代码与该规则冲突。  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## 示例  
 由于存在保护受保护类型的链接要求，因此应用程序无法创建实例。  下面的类使此应用程序能够获取受保护类型的实例。  
  
 [!CODE [FxCop.Security.LDOnFieldsDistributor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor#1)]  
  
## 示例  
 下面的应用程序阐释在没有权限访问受保护类型的方法的情况下，代码如何才能访问其字段。  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
 该示例产生下面的输出。  
  
  **Creating an instance of SecuredTypeWithFields.**  
**Secured type fields: 22, 33**  
**Changing secured type's field...**  
**Cached Object fields: 99, 33**   
## 相关规则  
 [CA1051：不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## 请参阅  
 [链接需求](../Topic/Link%20Demands.md)   
 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)