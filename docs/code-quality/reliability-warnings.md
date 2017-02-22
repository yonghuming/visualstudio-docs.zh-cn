---
title: "可靠性警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "警告, 可靠性"
  - "可靠性警告"
  - "托管代码的分析警告, 可靠性警告"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 可靠性警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可靠性警告支持库和应用程序的可靠性，例如，正确的内存和线程用法。  
  
## 本节内容  
  
|规则|说明|  
|--------|--------|  
|[CA2000：超出范围前释放对象](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|由于可能发生异常事件，导致对象的终结器无法运行，因此，应显式释放对象，以避免对该对象的所有引用超出范围。|  
|[CA2001：避免调用有问题的方法](../Topic/CA2001:%20Avoid%20calling%20problematic%20methods.md)|某个成员调用可能存在危险或有问题的方法。|  
|[CA2002：不要锁定具有弱标识的对象](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|当可以跨应用程序域边界直接进行访问对象时，则认为该对象具有弱标识。  对于尝试获取对具有弱标识的对象的锁的线程，该线程可能会被其他应用程序域中持有对同一对象的锁的另一线程所阻止。|  
|[CA2003：不要将纤程视为线程](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|托管线程被视为 Win32 线程。|  
|[CA2004：移除对 GC.KeepAlive 的调用](../Topic/CA2004:%20Remove%20calls%20to%20GC.KeepAlive.md)|如果转换为使用 SafeHandle，请移除所有对 GC.KeepAlive \(object\) 的调用。  在这种情况下，类不必调用 GC.KeepAlive，因为假定它们没有终结器，只是依赖 SafeHandle 来为它们完成 OS 句柄。|  
|[CA2006：使用 SafeHandle 封装本机资源](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|在托管代码中使用 IntPtr 可能意味着潜在的安全性和可靠性方面的问题。  必须检查所有使用 IntPtr 之处，以确定是否需要在该处使用 SafeHandle 或类似的技术。|