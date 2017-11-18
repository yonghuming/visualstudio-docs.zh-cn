---
title: "CA2001： 避免调用有问题的方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ca28bc1fd6a76262b47800dcca466e8843d3271
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001：避免调用有问题的方法
|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|CheckId|CA2001|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 某个成员调用可能存在危险或有问题的方法。  
  
## <a name="rule-description"></a>规则说明  
 避免进行不必要的潜在危险的方法调用。  
  
 某个成员调用以下方法之一，则会发生此规则的冲突。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|调用 GC。收集可能会显著影响应用程序性能，并很少需要。 有关详细信息，请参阅[多黎哥 Mariani 性能 Tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) MSDN 上的博客文章。|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend 和 Thread.Resume 已被否决由于其不可预知的行为。  使用中的其他类<xref:System.Threading>命名空间，如<xref:System.Threading.Monitor>， <xref:System.Threading.Mutex>， <xref:System.Threading.Mutex>，和<xref:System.Threading.Semaphore>以同步线程或保护资源。|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle 方法会带来安全风险，因为它可以返回不是有效的句柄。 请参阅<xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>和<xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>有关如何安全地使用 DangerousGetHandle 方法的详细信息的方法。|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|这些方法可以从意外的位置加载程序集。 有关示例，请参阅呢 Cook.NET CLR 说明博客文章[LoadFile vs。LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450)和[选择绑定上下文](http://go.microsoft.com/fwlink/?LinkId=164451)有关加载程序集的方法信息 MSDN 网站上。|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|由用户代码开始在托管进程中执行的时，它是太迟可靠地调用 CoSetProxyBlanket。 公共语言运行时 (CLR) 执行可能会阻止用户 P/Invoke 之后的初始化操作。<br /><br /> 如果需要调用 CoSetProxyBlanket 托管的应用程序，我们建议你通过使用本机代码 （c + +） 可执行文件启动过程、 在本机代码中，调用 CoSetProxyBlanket，然后在进程中启动托管的代码应用程序。 （请务必指定运行时的版本号。）|  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除或替换对危险或有问题的方法的调用。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 仅当有问题的方法没有替代项时可用，则应该禁止显示此规则的消息。  
  
## <a name="see-also"></a>另请参阅  
 [可靠性警告](../code-quality/reliability-warnings.md)