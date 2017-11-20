---
title: "CA1403： 自动布局类型不应对 COM 可见 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e5f8617b7ed5f0bec9ecaa2f4fbca1653cee46f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403：自动布局类型不应对 COM 可见
|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|类别|Microsoft.Interoperability|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 组件对象模型 (COM) 可见值类型将标有<xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>属性设置为<xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 <xref:System.Runtime.InteropServices.LayoutKind>由公共语言运行时管理布局类型。 这些类型的布局可以将中断要求特定布局的 COM 客户端的.NET framework 的版本之间发生更改。 请注意，如果<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性未指定，C# 中， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，和 c + + 编译器指定<xref:System.Runtime.InteropServices.LayoutKind>为值类型的布局。  
  
 除非以其他方式标记，所有公共的非泛型类型都是对 COM 可见所有的非公共和泛型类型不可见给 com。 但是，若要减少误报，此规则要求要明确表述; 的类型的 COM 可见包含程序集都必须标记为<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>设置为`false`和类型都必须标记为<xref:System.Runtime.InteropServices.ComVisibleAttribute>设置为`true`。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将更改的值<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性设为<xref:System.Runtime.InteropServices.LayoutKind>或<xref:System.Runtime.InteropServices.LayoutKind>，或使该类型对 COM 可见  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示满足该规则的类型和类型的与该规则冲突。  
  
 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1408：请不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>另请参阅  
 [类接口简介](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [为互操作限定 .NET 类型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [与非托管代码交互操作](/dotnet/framework/interop/index)