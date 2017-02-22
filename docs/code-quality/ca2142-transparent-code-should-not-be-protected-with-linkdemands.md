---
title: "CA2142：不应使用 LinkDemand 保护透明代码 | Microsoft Docs"
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
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2142：不应使用 LinkDemand 保护透明代码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 透明方法需要 <xref:System.Security.Permissions.SecurityAction> 或其他安全要求。  
  
## 规则说明  
 对于需要 LinkDemand 来访问它们的透明方法，将会引发此规则。  安全透明代码不应负责验证某个操作的安全，因此不应要求权限。  因为透明方法不会受安全性影响，所以它们不应作出任何安全决策。  此外，确实会作出安全决策的安全关键代码不应依赖透明代码实现作出这种决策。  
  
## 如何解决冲突  
 修复与该规则的冲突，删除透明的方法上的链接要求或用 <xref:System.Security.SecuritySafeCriticalAttribute> 标记方法，前提是它执行安全检查，如安全要求。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 在下面的示例中，规则在方法上激发，因为该方法是透明的并且标记为包含<xref:System.Security.Permissions.SecurityAction>的LinkDemand <xref:System.Security.PermissionSet> 。  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 不要禁止显示此规则发出的警告。