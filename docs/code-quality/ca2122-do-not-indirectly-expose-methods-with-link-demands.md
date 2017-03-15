---
title: "CA2122：不要使用链接请求间接公开方法 | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122：不要使用链接请求间接公开方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|类别|Microsoft.Security|  
|是否重大更改|否|  
  
## 原因  
 公共或受保护成员具有 [链接需求](../Topic/Link%20Demands.md)，且是由不执行任何安全检查的成员调用的。  
  
## 规则说明  
 链接请求仅检查直接调用方的权限。  如果成员 `X` 不发出其调用方的安全请求，并调用受链接请求保护的代码，则没有必需权限的调用方可使用 `X` 访问受保护成员。  
  
## 如何解决冲突  
 向成员添加安全 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) 或链接请求，使其不再提供对受链接请求保护的成员的不安全访问。  
  
## 何时禁止显示警告  
 若要安全禁止显示此规则发出的警告，必须确保您的代码不会授予其调用方对可通过破坏性方式使用的操作或资源的访问权限。  
  
## 示例  
 下面的示例显示一个与该规则冲突的库以及一个演示该库漏洞的应用程序。  示例库提供一起与该规则冲突的两个方法。  `EnvironmentSetting` 方法受链接请求保护，可无限制地访问环境变量。  `DomainInformation` 方法在调用 `EnvironmentSetting` 之前，不会对其调用方提出任何安全请求。  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## 示例  
 下面的应用程序调用不安全的库成员。  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 该示例产生下面的输出。  
  
  **Value from unsecured member: seattle.corp.contoso.com**   
## 请参阅  
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)   
 [链接需求](../Topic/Link%20Demands.md)   
 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)