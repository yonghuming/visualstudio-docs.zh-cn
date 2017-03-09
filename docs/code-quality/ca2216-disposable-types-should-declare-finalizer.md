---
title: "CA2216：可释放类型应声明终结器 | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216：可释放类型应声明终结器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 实现 <xref:System.IDisposable?displayProperty=fullName> 并包含建议使用非托管资源的字段的类型未实现 <xref:System.Object.Finalize%2A?displayProperty=fullName> 所描述的终结器。  
  
## 规则说明  
 如果可释放类型包含以下类型的字段，则将报告与该规则的冲突：  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## 如何解决冲突  
 要修复与该规则的冲突，请实现一个终结器来调用您的 <xref:System.IDisposable.Dispose%2A> 方法。  
  
## 何时禁止显示警告  
 如果类型没有实现 <xref:System.IDisposable> 来释放非托管资源，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## 相关规则  
 [CA2115：使用本机资源时调用 GC.KeepAlive](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816：正确调用 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049：拥有本机资源的类型应是可释放的](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## 请参阅  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [释放模式](../Topic/Dispose%20Pattern.md)