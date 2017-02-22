---
title: "CA2138：透明方法不得调用具有 SuppressUnmanagedCodeSecurity 特性的方法 | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138：透明方法不得调用具有 SuppressUnmanagedCodeSecurity 特性的方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 安全透明方法调用用 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 特性标记的方法。  
  
## 规则说明  
 此规则触发任何透明的方法，其直接调用到本机代码中，例如通过使用 P\/invoke（平台调用）调用。  标记为 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 特性的 P\/invoke 和 COM 互操作方法将在调用方法中触发 LinkDemand。  因为安全透明代码不能满足 LinkDemands，该代码也不能调用用 SuppressUnmanagedCodeSecurity 特性标记的方法，或调用用 SuppressUnmanagedCodeSecurity 特性标记的方法或类。  该方法将失败，或该要求将被转换为完整的请求。  
  
 违反该规则会导致级别 2 安全透明模型中的 <xref:System.MethodAccessException>，以及级别 1 透明度模型中的 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 的完全要求。  
  
## 如何解决冲突  
 要解决此规则的冲突，删除 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 特性，或使用 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 特性标记方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]