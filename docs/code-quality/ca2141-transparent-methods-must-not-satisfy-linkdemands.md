---
title: "CA2141：透明方法不得满足 LinkDemand | Microsoft Docs"
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
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2141：透明方法不得满足 LinkDemand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 安全透明方法调用未用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) 特性标记的程序集中的方法，或者安全透明方法满足<xref:System.Security.Permissions.SecurityAction>`.LinkDemand` 的类型或方法。  
  
## 规则说明  
 满足 LinkDemand 是一个安全敏感操作，这可能导致权限意外提升。  安全透明代码不必满足 LinkDemands，因为它不服从于与安全关键代码相同的安全审核要求。  在安全规则集 1 级程序集的透明方法将导致它们满足的所有 LinkDemands 在运行时转换为完整的需求，这可能导致性能问题。  安全规则集 2 级程序集将无法编译中实时 \(JIT\) 编译器中，如果他们尝试满足 LinkDemand 透明的方法。  
  
 在安全级别为 2 级的程序集中，尝试满足 LinkDemand 的安全透明方法或在非 APTCA 程序集调用一个方法将引发 <xref:System.MethodAccessException>；在安全级别为 1 级的程序集中，LinkDemand 成为完整的请求。  
  
## 如何解决冲突  
 要解决此规则的冲突，使用 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 特性标记访问方法，或从访问的方法删除 LinkDemand。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 在此示例中，透明的方法将尝试调用具有 LinkDemand 的方法。  此规则将在此代码上被激发。  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]