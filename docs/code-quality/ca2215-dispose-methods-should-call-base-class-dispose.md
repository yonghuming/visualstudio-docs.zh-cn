---
title: "CA2215：Dispose 方法应调用基类的 Dispose | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215：Dispose 方法应调用基类的 Dispose
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 实现 <xref:System.IDisposable?displayProperty=fullName> 的类型继承自同时实现 <xref:System.IDisposable> 的类型。  继承类型的 <xref:System.IDisposable.Dispose%2A> 方法未调用父类型的 <xref:System.IDisposable.Dispose%2A> 方法。  
  
## 规则说明  
 如果类型继承自可释放类型，则必须从它自己的 <xref:System.IDisposable.Dispose%2A> 方法中调用基类型的 <xref:System.IDisposable.Dispose%2A> 方法。  调用基类型方法 Dispose 可以确保释放由基类型创建的任何资源。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请调用您的 <xref:System.IDisposable.Dispose%2A> 方法中的 `base`.<xref:System.IDisposable.Dispose%2A>。  
  
## 何时禁止显示警告  
 如果对 `base`.<xref:System.IDisposable.Dispose%2A> 的调用发生在比规则检查更深的调用级别，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示实现 <xref:System.IDisposable> 的类型 `TypeA`。  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## 示例  
 下面的示例演示类型 `TypeB`，该类型继承自类型 `TypeA` 并正确地调用其 <xref:System.IDisposable.Dispose%2A> 方法。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_1.vb)]  
  
## 请参阅  
 <xref:System.IDisposable?displayProperty=fullName>   
 [释放模式](../Topic/Dispose%20Pattern.md)