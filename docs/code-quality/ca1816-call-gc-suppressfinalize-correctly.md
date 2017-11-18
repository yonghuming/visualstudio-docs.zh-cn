---
title: "CA1816： 调用 GC。SuppressFinalize 正确 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e99f722d211b2e1bd548f1bf22c995246f3e0b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816：正确调用 GC.SuppressFinalize
|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|类别|Microsoft。 用法|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
  
-   实现的方法<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>不调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   不是实现的方法<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   一个方法调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>并传递 this (Me 以外在 Visual Basic 中）。  
  
## <a name="rule-description"></a>规则说明  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法可让用户在任何时间变得可用于垃圾回收的对象之前释放资源。 如果<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法调用，因此它释放的对象的资源。 这使得无需终止。 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>应调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>以便垃圾回收器不会调用的对象的终结器。  
  
 若要防止具有终结器的派生的类型无需重新实现<xref:System.IDisposable>和调用它，未密封的类型没有终结器应仍调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突：  
  
 如果此方法的实现<xref:System.IDisposable.Dispose%2A>，添加对的调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
 如果此方法不是实现<xref:System.IDisposable.Dispose%2A>，或者移除对的调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>或将其移到该类型的<xref:System.IDisposable.Dispose%2A>实现。  
  
 更改所有调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>传递 this (Me 在 Visual Basic 中)。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果你考虑使用仅禁止显示此规则的警告<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>来控制的其他对象的生存期。 如果的实现不禁止显示此规则的警告<xref:System.IDisposable.Dispose%2A>不调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。 在这种情况下，如果取消终止失败会降低性能，并不提供任何好处。  
  
## <a name="example"></a>示例  
 下面的示例显示了一种方法未正确调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>示例  
 下面的示例的演示一种方法，它正确调用<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2215：Dispose 方法应调用基类 Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216：可释放类型应声明终结器](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>另请参阅  
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)