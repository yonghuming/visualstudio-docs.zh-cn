---
title: "CA2106：保护断言 | Microsoft Docs"
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
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106：保护断言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SecureAsserts|  
|CheckId|CA2106|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 某个方法断言权限，但不对调用方执行任何安全检查。  
  
## 规则说明  
 如果在不执行任何安全检查的情况下断言安全权限，则会在代码中留下可利用的安全漏洞。  断言安全权限后，安全堆栈审核随即停止。  如果在不对调用方执行任何检查的情况下断言权限，则该调用方可以使用您的权限来间接地执行代码。  只有当您确保不会以有害的方式使用断言时，才能允许无安全检查的断言。  如果您调用的代码是无害的，断言就是无害的，否则，用户无法将任意信息传递给您调用的代码。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请向该方法或其声明类型中添加安全请求。  
  
## 何时禁止显示警告  
 只有在仔细检查安全性之后，才能禁止显示此规则发出的警告。  
  
## 请参阅  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)