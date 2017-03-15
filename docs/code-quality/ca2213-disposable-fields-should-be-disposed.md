---
title: "CA2213：应释放可释放的字段 | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213：应释放可释放的字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 实现 <xref:System.IDisposable?displayProperty=fullName> 的类型声明同样实现 <xref:System.IDisposable> 的类型的字段。  字段的 <xref:System.IDisposable.Dispose%2A> 方法不是由声明类型的 <xref:System.IDisposable.Dispose%2A> 方法调用。  
  
## 规则说明  
 类型负责释放其全部非托管资源，这是通过实现 <xref:System.IDisposable> 完成的。  该规则进行检查，以确定可释放类型 `T` 是否声明字段 `F`，该字段为可释放类型 `FT` 的实例。  对于每个字段 `F`，该规则尝试定位对 `FT.Dispose` 的调用。  该规则搜索 `T.Dispose` 调用的方法及下一级方法（由 `FT.Dispose` 调用的方法所调用的方法）。  
  
## 如何解决冲突  
 要修复与该规则的冲突，如果您负责分配和释放字段中包含的非托管资源，请在实现 <xref:System.IDisposable> 的类型的字段上调用 <xref:System.IDisposable.Dispose%2A>。  
  
## 何时禁止显示警告  
 如果您不负责释放字段包含的资源，或者对 <xref:System.IDisposable.Dispose%2A> 的调用发生在该规则所检查的调用级别以下的级别中，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示实现 <xref:System.IDisposable>（上文中讨论的 `FT`）的类型 `TypeA`。  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## 示例  
 以下示例示出了违背该规则的类型 `TypeB`，方法是将字段 `aFieldOfADisposableType`（前面讨论的 `F`）声明为可释放类型 \(`TypeA`\)，并且不调用字段上的 <xref:System.IDisposable.Dispose%2A>。  `TypeB` 对应于前面讨论中的 `T`。  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## 请参阅  
 <xref:System.IDisposable?displayProperty=fullName>   
 [释放模式](../Topic/Dispose%20Pattern.md)