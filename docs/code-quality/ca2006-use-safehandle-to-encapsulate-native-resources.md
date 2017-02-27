---
title: "CA2006：使用 SafeHandle 封装本机资源 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2006：使用 SafeHandle 封装本机资源
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大更改|  
  
## 原因  
 托管代码使用 <xref:System.IntPtr> 访问本机资源。  
  
## 规则说明  
 在托管代码中使用 `IntPtr` 可能意味着潜在的安全性和可靠性方面的问题。  必须检查所有使用 `IntPtr` 之处，以确定是否需要在该处使用 <xref:System.Runtime.InteropServices.SafeHandle> 或类似的技术。  如果 `IntPtr` 表示某些被视为由托管代码所有的本机资源，如内存、文件句柄或套接字等，则会发生问题。  如果托管的代码拥有资源，它还必须释放与其关联的本机资源，因为无法执行此操作将导致资源泄漏。  
  
 在这样的情况下，如果允许对 `IntPtr` 进行多线程访问且提供一种由 `IntPtr` 表示的释放资源的方法，则还会存在安全性和可靠性方面的问题。  这些问题包括在资源释放时回收 `IntPtr` 值，而与此同时另一个线程上正在使用该资源。  这可能导致争用条件，其中一个线程可以读取或写入与错误资源关联的数据。  例如，如果您的类型将某个操作系统句柄存储为一个 `IntPtr`，并且既允许用户调用 **Close**，又允许用户在不采用任何类型的同步的情况下调用同时使用该句柄的其他任何方法，则您的代码存在句柄回收问题。  
  
 此句柄回收问题可能会导致数据损坏，并且经常会导致安全漏洞。  `SafeHandle` 及其同级类 <xref:System.Runtime.InteropServices.CriticalHandle> 提供了一种封装资源的本机句柄的机制，从而可以避免此类线程问题。  另外，还可以使用 `SafeHandle` 及其同级类 `CriticalHandle` 来避免其他线程问题，例如，通过调用本机方法来仔细控制包含本机句柄副本的托管对象的生存期。  在这种情况下，通常可以移除对 `GC.KeepAlive` 的调用。  使用 `SafeHandle` 时会导致性能开销（`CriticalHandle` 也有同样的问题，但程度要轻一些），通过仔细设计通常可以减少这些开销。  
  
## 如何解决冲突  
 将所使用的 `IntPtr` 转换为 `SafeHandle` 以安全地管理对本机资源的访问。  有关示例，请参见 <xref:System.Runtime.InteropServices.SafeHandle> 参考主题。  
  
## 何时禁止显示警告  
 不应禁止显示此警告。  
  
## 请参阅  
 <xref:System.IDisposable>