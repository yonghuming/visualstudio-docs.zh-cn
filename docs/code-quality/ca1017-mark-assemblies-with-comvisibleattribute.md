---
title: "CA1017： 将程序集用 ComVisibleAttribute 标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e4c76efff009c85f9d607611d92d53cad5d2759
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017：用 ComVisibleAttribute 标记程序集
|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 程序集没有<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>特性应用于它。  
  
## <a name="rule-description"></a>规则说明  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>属性确定 COM 客户端如何访问托管的代码。 合理的设计指出程序集将显式指示 COM 可见性。 COM 可见性可进行设置整个程序集，然后重写各个类型和类型成员。 如果属性不存在，则程序集的内容是对 COM 客户端可见。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将添加到程序集的属性。 如果你不想要对 COM 客户端可见的程序集，应用该特性并将其值设置为`false`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 如果你想要显示的程序集，应用该特性并将其值设置为`true`。  
  
## <a name="example"></a>示例  
 下面的示例演示具有的程序集<xref:System.Runtime.InteropServices.ComVisibleAttribute>应用以防止它对 COM 客户端可见属性。  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](/dotnet/framework/interop/index)   
 [为互操作限定 .NET 类型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)