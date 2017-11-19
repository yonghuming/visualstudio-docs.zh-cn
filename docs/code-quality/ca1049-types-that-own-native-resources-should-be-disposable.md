---
title: "CA1049： 拥有本机资源的类型应该是可释放 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ebcb3325cfefdfeeb95b30477c4b266a70f40eb0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049：拥有本机资源的类型应是可释放的
|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 一种类型引用<xref:System.IntPtr?displayProperty=fullName>字段，<xref:System.UIntPtr?displayProperty=fullName>字段，或<xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>字段，但不实施<xref:System.IDisposable?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 此规则假定<xref:System.IntPtr>， <xref:System.UIntPtr>，和<xref:System.Runtime.InteropServices.HandleRef>字段存储指向非托管资源。 分配非托管的资源的类型应该实现<xref:System.IDisposable>以使调用方以释放这些资源按需并缩短持有这些资源的对象的生存期。  
  
 要清理非托管资源的推荐的设计模式是提供一种隐式和显式方式使用释放这些资源<xref:System.Object.Finalize%2A?displayProperty=fullName>方法和<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法，分别。 垃圾回收器调用<xref:System.Object.Finalize%2A>处一些不确定的时间之后确定该对象为不再可访问的对象的方法。 后<xref:System.Object.Finalize%2A>调用时，附加释放该对象所需的垃圾回收。 <xref:System.IDisposable.Dispose%2A>方法允许调用方显式释放这些资源按需、 早于如果留给垃圾回收器将释放资源。 清理非托管资源之后,<xref:System.IDisposable.Dispose%2A>应调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>方法以允许垃圾回收器知道<xref:System.Object.Finalize%2A>不再具有要调用; 这可以避免需要附加的垃圾回收并缩短对象生存期。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，实现<xref:System.IDisposable>。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果类型未引用非托管的资源。 否则，不要禁止显示此规则的警告因为无法实现<xref:System.IDisposable>可能会导致非托管的资源变得不可用或未被充分利用。  
  
## <a name="example"></a>示例  
 下面的示例演示一个实现类型<xref:System.IDisposable>清理非托管资源。  
  
 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2115：使用本机资源时调用 GC.KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816：正确调用 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216：可释放类型应声明终结器](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001：具有可释放字段的类型应该是可释放的](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  
  
## <a name="see-also"></a>另请参阅  
 [清理非托管资源](/dotnet/standard/garbage-collection/unmanaged)   
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)