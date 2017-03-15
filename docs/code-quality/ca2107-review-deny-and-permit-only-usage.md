---
title: "CA2107：检查 deny 权限和 permit only 权限的使用情况 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107：检查 deny 权限和 permit only 权限的使用情况
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 某方法包含指定 PermitOnly 或 Deny 安全操作的安全检查。  
  
## 规则说明  
 [Using the PermitOnly Method](http://msdn.microsoft.com/zh-cn/8c7bdb7f-882f-45b7-908c-6cbaa1767649) 和 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> 安全操作应仅由掌握高级 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 安全性知识的人员使用。  应当对使用这些安全操作的代码进行安全检查。  
  
 Deny 会更改为响应安全请求而发生的堆栈审核的默认行为。  它允许您指定在拒绝方法的持续时间内不得授予的权限，而无论调用方在调用堆栈中实际具有何种权限。  如果堆栈审核检测到由 Deny 保护的方法，且所请求权限包含在已拒绝权限中，则堆栈审核失败。  PermitOnly 也会更改堆栈审核的默认行为。  它允许代码仅指定那些能够被授予的权限，而无论调用方具有何种权限。  如果堆栈审核检测到由 PermitOnly 保护的方法，且所请求的权限未包含在 PermitOnly 指定的权限中，则堆栈审核失败。  
  
 因为用途有限且行为难以捉摸，应认真评估依赖这些操作的代码是否存在安全漏洞。  考虑以下情况：  
  
-   [链接需求](../Topic/Link%20Demands.md) 不受 Deny 或 PermitOnly 影响。  
  
-   如果 Deny 或 PermitOnly 与导致堆栈审核的请求发生在同一堆栈框架中，则安全操作不产生任何影响。  
  
-   通常情况下，可通过多种方法指定用于构造基于路径的权限的值。  对一种形式的路径的拒绝访问不会拒绝对所有形式的路径的访问。  例如，如果文件共享 \\\\Server\\Share 映射到网络驱动器 X:，则要拒绝对共享中文件的访问，必须拒绝 \\\\Server\\Share\\File、X:\\File 和访问该文件的其他每个路径。  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> 可在到达 Deny 或 PermitOnly 之前终止堆栈审核。  
  
-   如果 Deny 会产生影响，即调用方具有 Deny 所阻止的权限，则调用方可跳过 Deny 直接访问受保护资源。  同样，如果调用方不具有被拒绝的权限，则即使不存在 Deny，堆栈审核也会失败。  
  
## 如何解决冲突  
 只要使用上述安全操作，就会导致冲突。  若要修复冲突，请不要使用这些安全操作。  
  
## 何时禁止显示警告  
 仅在完成安全检查后，才能禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示 Deny 的部分限制。  
  
 下面的库包含一个类，该类包含两个相同方法，二者的唯一区别是保护它们的安全请求不同。  
  
 [!CODE [FxCop.Security.PermitAndDeny#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny#1)]  
  
## 示例  
 下面的应用程序演示 Deny 对库中的受保护方法的影响。  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
 该示例产生下面的输出。  
  
  **Demand: Caller's Deny has no effect on Demand with the asserted permission.**  
**LinkDemand：调用方的拒绝对具有断言权限的 LinkDemand 不起作用。**  
**LinkDemand：调用方的拒绝对受 LinkDemand 保护的代码不起作用。**  
**LinkDemand：此拒绝对受 LinkDemand 保护的代码不起作用。**   
## 请参阅  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/zh-cn/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/zh-cn/8c7bdb7f-882f-45b7-908c-6cbaa1767649)