---
title: "CA2145：不应使用 SuppressUnmanagedCodeSecurityAttribute 修饰透明方法 | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145：不应使用 SuppressUnmanagedCodeSecurityAttribute 修饰透明方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 安全透明方法就是用 <xref:System.Security.SecuritySafeCriticalAttribute> 方法标记的方法，或者说包含用 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 特性标记的方法的类型。  
  
## 规则说明  
 用 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 特性修饰的方法有一个隐式的 LinkDemand 作用于调用它的任何方法。  此 LinkDemand 要求调用代码是关键安全的。  将标记对 SuppressUnmanagedCodeSecurity 使用 <xref:System.Security.SecurityCriticalAttribute> 特性的方法使此要求对方法的调用方更加明显。  
  
## 如何解决冲突  
 要修复该规则的冲突，用 <xref:System.Security.SecurityCriticalAttribute> 特性标记该方法或类型。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
### 代码  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### 注释