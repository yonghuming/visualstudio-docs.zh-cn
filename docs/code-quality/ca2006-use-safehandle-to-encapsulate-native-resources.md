---
title: "CA2006： 使用 SafeHandle 封装本机资源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b83aec0a44e0762ed2d65f9bbbd39318b1b1b942
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006：使用 SafeHandle 封装本机资源
|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 托管代码使用<xref:System.IntPtr>来访问该本机资源。  
  
## <a name="rule-description"></a>规则说明  
 利用`IntPtr`在托管代码中可能意味着潜在的安全性和可靠性问题。 所有使用`IntPtr`必须可以检查以确定是否使用<xref:System.Runtime.InteropServices.SafeHandle>，或类似技术，需要在该处。 如果，则会发生问题`IntPtr`代表某些本机资源，如内存、 文件句柄或套接字，托管的代码被视为拥有。 如果托管的代码拥有的资源，它还必须释放与之关联的本机资源，因为未能这样做可能会导致资源泄漏。  
  
 在这种情况下，安全性或可靠性问题还会存在如果允许对多线程的访问`IntPtr`和释放资源所表示的一种方法`IntPtr`提供。 这些问题涉及回收`IntPtr`在资源释放时同时使用的资源正在进行另一个线程上的值。 这可能导致争用条件，其中一个线程可以读取或写入错误的资源与关联的数据。 例如，如果你的类型将作为 OS 句柄存储`IntPtr`并允许用户请同时调用**关闭**和任何其他方法使用该句柄，同时和不同步的某种类型的情况下，你的代码有回收的句柄问题。  
  
 此句柄回收问题可能导致数据损坏和，通常情况下，安全漏洞。 `SafeHandle`和其同级类<xref:System.Runtime.InteropServices.CriticalHandle>提供一种机制来封装对资源的本机句柄，以便可以避免此类线程处理问题。 此外，你可以使用`SafeHandle`和其同级类`CriticalHandle`有关其他线程处理问题，例如，若要仔细控制对本机方法的调用中包含的本机句柄的副本的托管对象的生存期。 在此情况下，你通常可以消除对调用`GC.KeepAlive`。 使用时产生性能系统开销也`SafeHandle`和一定程度上， `CriticalHandle`，通常可以通过仔细设计减少。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 将转换`IntPtr`使用情况与`SafeHandle`以便安全地管理对本机资源的访问。 请参阅<xref:System.Runtime.InteropServices.SafeHandle>示例的参考主题。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不应禁止显示此警告。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IDisposable>