---
title: "CA2114：方法安全性应是类型安全性的超集 | Microsoft Docs"
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
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114：方法安全性应是类型安全性的超集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 某类型有声明性安全，它的某个方法有同一安全操作的声明性安全，该安全操作不是 [链接需求](../Topic/Link%20Demands.md) 或 [Inheritance Demands](http://msdn.microsoft.com/zh-cn/28b9adbb-8f08-4f10-b856-dbf59eb932d9)，类型检查的权限也不是该方法检查的权限的子集。  
  
## 规则说明  
 某方法不应同时有同一操作的方法级别和类型级别的声明性安全。  两种检查不会合并；只会应用方法级别的要求。  例如，如果一个类型要求具备权限 `X`，而它的某个方法要求具备权限 `Y`，则代码不需要具备权限 `X` 就可以执行该方法。  
  
## 如何解决冲突  
 检查代码以确保同时需要这两种操作。  如果同时需要这两种操作，请确保方法级别的操作包含类型级别指定的安全性。  例如，如果类型要求权限 `X`，而其方法必须要求权限 `Y`，则该方法应当显式要求 `X` 和 `Y`。  
  
## 何时禁止显示警告  
 如果方法不需要类型指定的安全性，则可以安全地禁止显示此规则发出的警告。  然而，这并不是一种正常的情况，可能表示需要进行仔细的设计检查。  
  
## 示例  
 下面的示例使用环境权限演示与该规则冲突的危险。  在此示例中，应用程序代码在拒绝类型要求的权限之前创建安全类型的实例。  在现实威胁情况中，应用程序将需要另一种获取对象实例的方法。  
  
 在下面的示例中，库要求类型有写权限，方法有读权限。  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## 示例  
 下面的应用程序代码通过调用方法（尽管该方法不能满足类型级别的安全要求）演示库的漏洞。  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 该示例产生下面的输出。  
  
  **\[All permissions\] Personal information: 6\/16\/1964 12:00:00 AM**  
**\[No write permission \(demanded by type\)\] Personal information: 6\/16\/1964 12:00:00 AM**  
**\[No read permission \(demanded by method\)\] Could not access personal information: Request failed.**   
## 请参阅  
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/zh-cn/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [链接需求](../Topic/Link%20Demands.md)   
 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)