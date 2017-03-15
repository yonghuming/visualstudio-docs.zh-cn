---
title: "CA2147：透明方法不得使用安全断言 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2147：透明方法不得使用安全断言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 标为 <xref:System.Security.SecurityTransparentAttribute> 的代码未被授予足够的权限进行断言。  
  
## 规则说明  
 此规则分析完全透明或混合透明\/关键的程序集中的所有方法和类型，并标记 <xref:System.Security.CodeAccessPermission.Assert%2A> 的任何声明性或命令性用法。  
  
 在运行时，从透明代码中对 <xref:System.Security.CodeAccessPermission.Assert%2A> 进行任何调用都会导致引发 <xref:System.InvalidOperationException>。  此种情况在完全透明的程序集以及混合透明\/关键程序集（其中的某个方法或类型被声明为透明，但包括声明性或命令性 Assert）中都会发生这种情况。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 引入了一个称为“透明度”的功能。  各个方法、字段、接口、类和类型都可以是透明或关键的。  
  
 不允许透明代码提升安全特权。  因此，授予透明代码或其请求的任何权限都会自动通过该代码传递给调用方或主机应用程序域。  提升的示例包括 Assert、LinkDemand、SuppressUnmanagedCode 和`unsafe`代码。  
  
## 如何解决冲突  
 若要解决此问题，请将调用 Assert 的代码标记为 <xref:System.Security.SecurityCriticalAttribute>，或者删除该 Assert。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的消息。  
  
## 示例  
 当 `Assert` 方法引发 <xref:System.InvalidOperationException> 时，如果 `SecurityTestClass` 透明，此代码将失败。  
  
 [!CODE [FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts#1)]  
  
## 示例  
 其中一个选项是在以下示例中代码评审 SecurityTransparentMethod 方法，如果被认为可以安全提升，将 SecurityTransparentMethod 标记为可靠关键。这要求对在Assert 方法内发生的任何调用一起进行详细、完整和无错误的安全审核：  
  
 [!CODE [FxCop.Security.SecurityTransparentCode2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2#1)]  
  
 另一个方法是从代码中删除 Assert，并使任何后续的文件 I\/O 权限请求通过 SecurityTransparentMethod 流向调用方。  这可实现安全检查。  在此种情况下，一般不需要安全审核，因为权限请求将流向调用方和\/或应用程序域。  权限请求通过安全策略、宿主环境以及代码源权限授予进行严格的控制。  
  
## 请参阅  
 [安全警告](../code-quality/security-warnings.md)