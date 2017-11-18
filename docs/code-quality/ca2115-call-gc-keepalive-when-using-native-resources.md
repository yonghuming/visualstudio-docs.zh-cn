---
title: "CA2115： 调用 GC。使用本机资源时的 KeepAlive |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98833f1feccd70c3bdf140b4d2be7a4ad1a5d6bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115：使用本机资源时调用 GC.KeepAlive
|||  
|-|-|  
|TypeName|CallGCKeepAliveWhenUsingNativeResources|  
|CheckId|CA2115|  
|类别|Microsoft.Security|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 一种方法具有终结器的类型中声明引用<xref:System.IntPtr?displayProperty=fullName>或<xref:System.UIntPtr?displayProperty=fullName>字段，但不会调用<xref:System.GC.KeepAlive%2A?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 垃圾回收完成一个对象，如果在托管代码中没有更多引用。 对对象的非托管的引用不会妨碍垃圾回收。 该规则检测由于在非托管代码仍在使用非托管资源时终止该非托管资源而可能发生的错误。  
  
 此规则假定<xref:System.IntPtr>和<xref:System.UIntPtr>字段存储指向非托管资源。 由于终结器的用途是释放非托管的资源，该规则将假定终结器将释放的指针字段指向非托管的资源。 此规则还假定该方法引用要传递给非托管代码的非托管的资源的指针字段。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，添加到调用<xref:System.GC.KeepAlive%2A>当前实例传递给方法，(`this`以 C# 和 c + +) 作为自变量。 将该调用放在代码的最后一行后对象必须防止垃圾回收。 在调用后立即<xref:System.GC.KeepAlive%2A>，该对象再次被视为准备好进行垃圾回收假定没有托管的引用。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 此规则将进行某些假设，可能会导致误报。 如果，可以安全地禁止显示此规则的警告：  
  
-   终结器不会释放的内容<xref:System.IntPtr>或<xref:System.UIntPtr>方法引用的字段。  
  
-   该方法不能通过<xref:System.IntPtr>或<xref:System.UIntPtr>字段到非托管代码。  
  
 在中排除它们之前，请仔细查看其他消息。 此规则检测难以重现和调试的错误。  
  
## <a name="example"></a>示例  
 在下面的示例中，`BadMethod` 不包含对 `GC.KeepAlive` 的调用，因此违反了此规则。 `GoodMethod`包含更正后的代码。  
  
> [!NOTE]
>  尽管代码可以编译运行，但本示例是伪代码，之所以不引发警告是因为未创建或释放非托管资源。  
  
 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)