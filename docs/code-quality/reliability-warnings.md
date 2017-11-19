---
title: "可靠性警告 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3ac06911009a24640031fd3a2306110f289014f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="reliability-warnings"></a>可靠性警告
可靠性警告支持库和应用程序的可靠性，如使用正确的内存和线程。  
  
## <a name="in-this-section"></a>本节内容  
  
|规则|描述|  
|----------|-----------------|  
|[CA2000：超出范围前释放对象](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|由于可能发生异常事件，导致对象的终结器无法运行，因此，应显式释放对象，以避免对该对象的所有引用超出范围。|  
|[CA2001：避免调用有问题的方法](../code-quality/ca2001-avoid-calling-problematic-methods.md)|某个成员调用可能存在危险或有问题的方法。|  
|[CA2002：不要锁定具有弱标识的对象](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|当可以跨应用程序域边界直接进行访问对象时，则认为该对象具有弱标识。 对于尝试获取对具有弱标识的对象的锁的线程，该线程可能会被其他应用程序域中持有对同一对象的锁的另一线程所阻止。|  
|[CA2003：不要将纤程视为线程](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|托管的线程被视为 Win32 线程。|  
|[CA2004：移除对 GC.KeepAlive 的调用](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|如果要转换为使用 SafeHandle，删除对 GC 的所有调用。KeepAlive （对象）。 在这种情况下，类不必调用 GC。KeepAlive，假定它们没有终结器，但依赖 SafeHandle 来完成 OS 句柄来它们。|  
|[CA2006：使用 SafeHandle 封装本机资源](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|在托管代码中使用 IntPtr 可能意味着潜在的安全性和可靠性方面的问题。 必须检查所有使用 IntPtr 之处，以确定是否需要在该处使用 SafeHandle 或类似的技术。|