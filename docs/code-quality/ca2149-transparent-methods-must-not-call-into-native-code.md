---
title: "CA2149：透明方法不得调入本机代码 | Microsoft Docs"
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
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2149：透明方法不得调入本机代码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 通过方法存根（如 P\/Invoke）调用本机函数的方法。  
  
## 规则说明  
 对于直接调用到本机代码中（例如通过使用 P\/Invoke）的任何透明方法，将引发此规则。  违反该规则会导致级别 2 安全模型中的 <xref:System.MethodAccessException>，以及级别 1 透明度模型中的 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 的完全要求。  
  
## 如何解决冲突  
 要解决此规则的冲突，使用 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 特性标记调用本机代码的方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 [!CODE [FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode#1)]