---
title: "CA1816：正确调用 GC.SuppressFinalize | Microsoft Docs"
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
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816：正确调用 GC.SuppressFinalize
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|类别|Microsoft.  用法|  
|是否重大更改|否|  
  
## 原因  
  
-   作为 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 的实现的方法没有调用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   不是 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 的实现的方法调用了 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   方法调用了 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 并传递 this（在 Visual Basic 中是 Me）以外的某个值。  
  
## 规则说明  
 使用 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法，用户可以在可将对象作为垃圾回收之前随时释放资源。  如果调用了 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法，此方法会释放对象的资源。  这使得无需终止。  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 应调用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 以使垃圾回收器不调用对象的终结器。  
  
 若要使带有终结器的派生类型无需重新实现 [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) 和调用它，不带终结器的非密封类型仍然应调用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请执行以下操作：  
  
 如果相应方法是 <xref:System.IDisposable.Dispose%2A> 的实现，请添加对 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的调用。  
  
 如果相应方法不是 <xref:System.IDisposable.Dispose%2A> 的实现，请移除对 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的调用或将其移到相应类型的 <xref:System.IDisposable.Dispose%2A> 实现中。  
  
 将对 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的所有调用更改为传递 this（在 Visual Basic 中是 Me）。  
  
## 何时禁止显示警告  
 只有在您考虑使用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 来控制其他对象的生存期时，才应禁止显示此规则发出的警告。  如果 <xref:System.IDisposable.Dispose%2A> 的实现没有调用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>，请勿禁止显示此规则发出的警告。  在这种情况下，如果取消终止失败，则会使性能下降且不会有任何好处。  
  
## 示例  
 下面的示例显示了一个未正确调用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的方法。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## 示例  
 下面的示例显示了一个正确调用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的方法。  
  
 [!CODE [FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1)]  
  
## 相关规则  
 [CA2215：Dispose 方法应调用基类的 Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216：可释放类型应声明终结器](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## 请参阅  
 [释放模式](../Topic/Dispose%20Pattern.md)