---
title: "CA2216： 可释放类型应声明终结器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 087df27916465b3ddba0b8e2c92bacf89dd33c1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216：可释放类型应声明终结器
|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 实现一种<xref:System.IDisposable?displayProperty=fullName>，且具有建议非托管资源的使用的字段，不实现终结器，如下所述<xref:System.Object.Finalize%2A?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 如果可释放类型包含以下类型的字段，则会报告此规则的冲突：  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，实现终结器来调用你<xref:System.IDisposable.Dispose%2A>方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果类型未实现<xref:System.IDisposable>用于释放非托管的资源。  
  
## <a name="example"></a>示例  
 下面的示例演示了违反此规则的类型。  
  
 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2115：使用本机资源时调用 GC.KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816：正确调用 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049：拥有本机资源的类型应可释放](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)