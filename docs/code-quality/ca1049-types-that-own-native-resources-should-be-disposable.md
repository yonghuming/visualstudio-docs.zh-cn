---
title: "CA1049：拥有本机资源的类型应是可释放的 | Microsoft Docs"
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
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049：拥有本机资源的类型应是可释放的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 某类型引用了 <xref:System.IntPtr?displayProperty=fullName> 字段、<xref:System.UIntPtr?displayProperty=fullName> 字段或 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> 字段，但无法实现 <xref:System.IDisposable?displayProperty=fullName>。  
  
## 规则说明  
 该规则假定 <xref:System.IntPtr>、<xref:System.UIntPtr> 和 <xref:System.Runtime.InteropServices.HandleRef> 字段存储指向非托管资源的指针。  分配非托管资源的类型应该实现 <xref:System.IDisposable>，以使调用方可以根据需要释放这些资源，并缩短持有这些资源的对象的生存期。  
  
 清理非托管资源的建议设计模式是分别使用 <xref:System.Object.Finalize%2A?displayProperty=fullName> 方法和 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法，以隐式和显式方式释放这些资源。  在确定某个对象已不可访问之后，垃圾回收器将在某个不确定的时间调用该对象的 <xref:System.Object.Finalize%2A> 方法。  在调用 <xref:System.Object.Finalize%2A> 之后，需要执行附加垃圾回收操作以释放该对象。  使用 <xref:System.IDisposable.Dispose%2A> 方法，调用方可以根据需要在垃圾回收器释放资源之前显式释放这些资源。  在清理非托管资源后，<xref:System.IDisposable.Dispose%2A> 必须调用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 方法以通知垃圾回收器不再需要调用 <xref:System.Object.Finalize%2A>；这样可以消除附加的垃圾回收操作，缩短对象的生存期。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请实现 <xref:System.IDisposable>。  
  
## 何时禁止显示警告  
 如果类型没有引用非托管资源，则可以安全地禁止显示此规则发出的警告。  否则，不要禁止显示此规则发出的警告，因为如果无法实现 <xref:System.IDisposable>，可能会导致非托管资源不可用或被占用。  
  
## 示例  
 下面的示例演示一个实现 <xref:System.IDisposable> 来清理非托管资源的类型。  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## 相关规则  
 [CA2115：使用本机资源时调用 GC.KeepAlive](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816：正确调用 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216：可释放类型应声明终结器](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001：具有可释放字段的类型应该是可释放的](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)  
  
## 请参阅  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [释放模式](../Topic/Dispose%20Pattern.md)