---
title: "CA1406： 避免对 Visual Basic 6 客户端的 Int64 参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10b02338b16dc3bd1c67e3ab11cdd02d3d1ef1be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406：避免对 Visual Basic 6 客户端使用 Int64 参数
|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|类别|Microsoft.Interoperability|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 专门标记为可见到组件对象模型 (COM) 声明的类型的成员，采用<xref:System.Int64?displayProperty=fullName>自变量。  
  
## <a name="rule-description"></a>规则说明  
 Visual Basic 6 COM 客户端不能访问 64 位整数。  
  
 默认情况下，以下是对 COM 可见： 程序集、 公共类型，公共类型中的公共实例成员和公共值类型的所有成员。 但是，若要减少误报，此规则要求要明确表述; 的类型的 COM 可见包含程序集都必须标记为<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>设置为`false`和类型都必须标记为<xref:System.Runtime.InteropServices.ComVisibleAttribute>设置为`true`。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则，其值可以始终表示为 32 位整数参数的冲突，将参数类型更改为<xref:System.Int32?displayProperty=fullName>。 如果参数的值可能大于可以表示为 32 位整数，将参数类型更改为<xref:System.Decimal?displayProperty=fullName>。 请注意，同时<xref:System.Single?displayProperty=fullName>和<xref:System.Double?displayProperty=fullName>丧失精度的上限范围的<xref:System.Int64>数据类型。 如果成员不是为了应对 COM 可见，则将其与标记<xref:System.Runtime.InteropServices.ComVisibleAttribute>设置为`false`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果它是某些 Visual Basic 6 COM 客户端将不访问类型。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的类型。  
  
 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1413：避免在 COM 可见值类型中使用非公共字段](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407：避免在 COM 可见类型中使用静态成员](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](/dotnet/framework/interop/index)   
 [Long 数据类型](/dotnet/visual-basic/language-reference/data-types/long-data-type)