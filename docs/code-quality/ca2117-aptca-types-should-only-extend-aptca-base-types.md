---
title: "CA2117：APTCA 类型应只扩展 APTCA 基类型 | Microsoft Docs"
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
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117：APTCA 类型应只扩展 APTCA 基类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 具有 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 特性的程序集中的公共或受保护类型继承自没有该特性的程序集中声明的类型。  
  
## 规则说明  
 默认情况下，具有强名称的程序集中的公共或受保护类型受到针对完全信任的 [Inheritance Demands](http://msdn.microsoft.com/zh-cn/28b9adbb-8f08-4f10-b856-dbf59eb932d9) 的显式保护。  用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) 特性标记的具有强名称的程序集没有此保护。  此特性禁用继承要求。  这样，将使在程序集中声明的公开类型可以由不具有完全信任的类型继承。  
  
 如果完全受信任的程序集具有 APTCA 特性，并且程序集中的类型所继承的类型不允许部分受信任的调用方，则可能会产生安全问题。  如果两个类型 `T1` 和 `T2` 符合下列情况，则恶意调用方可以使用类型 `T1` 绕过用于保护 `T2` 的隐式的完全信任继承要求：  
  
-   `T1` 是在具有 APTCA 特性的完全受信任的程序集中声明的公共类型。  
  
-   `T1` 继承自其程序集之外的类型 `T2`。  
  
-   `T2` 的程序集没有 APTCA 特性，因此不应该由部分信任的程序集中的类型继承。  
  
 部分信任的类型 `X` 可以从 `T1` 继承，后者赋予前者访问在 `T2` 中声明的继承成员的权限。  由于 `T2` 没有 APTCA 特性，因此，其直接派生类型 \(`T1`\) 必须满足针对完全信任的继承要求；`T1` 具有完全信任，因此满足该检查。  安全风险来自于：`X` 并不参与满足继承要求（保护 `T2` 不会被不受信任的子类继承）的过程。  出于该原因，具有 APTCA 特性的类型不能扩展没有该特性的类型。  
  
 另一个安全问题（可能是更常见的问题）是：由于程序员的错误，派生类型 \(`T1`\) 会公开要求完全信任的类型 \(`T2`\) 中的受保护成员。  发生这种情况时，不受信任的调用方能够访问到仅供完全受信任类型使用的信息。  
  
## 如何解决冲突  
 如果冲突报告的类型在不要求 APTCA 特性的程序集中，请移除该类型。  
  
 如果要求 APTCA 特性，请向类型添加一个针对完全信任的继承要求。  这样可以避免通过不受信任的类型进行继承。  
  
 可以通过将 APTCA 特性添加到由冲突报告的基类型的程序集来解决冲突。  要执行该操作，必须首先对程序集中的所有代码以及依赖该程序集的所有代码进行严格的安全审查。  
  
## 何时禁止显示警告  
 要安全地禁止显示此规则发出的警告，必须确保由您的类型公开的受保护成员不直接或间接地允许不受信任的调用方访问可通过破坏性方式使用的敏感信息、操作或资源。  
  
## 示例  
 下面的示例使用两个程序集和一个测试应用程序来阐释该规则检测到的安全漏洞。  第一个程序集没有 APTCA 特性，不应由部分受信任的类型继承（由前面讨论的 `T2` 表示）。  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## 示例  
 第二个程序集（由前面讨论的 `T1` 表示）是完全受信任的，允许部分受信任的调用方。  
  
 [!CODE [FxCop.Security.YesAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit#1)]  
  
## 示例  
 由前面讨论的 `X` 表示的测试类型位于部分受信任的程序集中。  
  
 [!CODE [FxCop.Security.TestAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit#1)]  
  
 该示例产生下面的输出。  
  
  **Meet at the shady glen 2\/22\/2003 12:00:00 AM\!**  
**From Test: sunny meadow**  
**Meet at the sunny meadow 2\/22\/2003 12:00:00 AM\!**   
## 相关规则  
 [CA2116：APTCA 方法应只调用 APTCA 方法](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)  
  
## 请参阅  
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/zh-cn/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [通过部分受信任的代码使用库](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/zh-cn/28b9adbb-8f08-4f10-b856-dbf59eb932d9)