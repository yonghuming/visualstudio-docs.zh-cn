---
title: "CA1414： 标记布尔型 P Invoke 自变量用 MarshalAs |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25fd80168e78feda70b86f512598a850acae7010
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414：用 MarshalAs 标记布尔型 P/Invoke 参数
|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|类别|Microsoft.Interoperability|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 平台调用方法声明中包含<xref:System.Boolean?displayProperty=fullName>参数或返回值但<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>属性不应用于参数或返回值。  
  
## <a name="rule-description"></a>规则说明  
 平台调用方法访问非托管的代码，而且使用定义`Declare`中的关键字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>指定用于托管和非托管代码之间转换数据类型的封送处理行为。 许多简单数据类型，如<xref:System.Byte?displayProperty=fullName>和<xref:System.Int32?displayProperty=fullName>、 在非托管代码中有一种表示形式和不需要其封送处理行为的规范; 公共语言运行时自动提供正确的行为。  
  
 <xref:System.Boolean>数据类型在非托管代码中有多种表示形式。 当<xref:System.Runtime.InteropServices.MarshalAsAttribute>未指定，默认封送处理行为<xref:System.Boolean>数据类型是<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 这是不适合在所有情况下的 32 位整数。 所需的非托管方法的 boolean 类型的值表示应进行确定和匹配到相应<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 UnmanagedType.Bool 是 Win32 BOOL 类型，这始终是 4 个字节。 UnmanagedType.U1 应该用于 c + +`bool`或其他 1 字节类型。 有关详细信息，请参阅[布尔值类型的默认封送处理](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将应用<xref:System.Runtime.InteropServices.MarshalAsAttribute>到<xref:System.Boolean>参数或返回值。 将该属性的值设置为相应<xref:System.Runtime.InteropServices.UnmanagedType>。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 即使封送处理行为的默认值是合适的仅当显式指定的行为，更轻松地将保持代码。  
  
## <a name="example"></a>示例  
 下面的示例演示两个平台调用标记有适当的方法<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性。  
  
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1901: P/Invoke 声明应为可移植](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101： 指定对 P/Invoke 字符串自变量封送处理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [默认为布尔值类型的封送处理](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [与非托管代码交互操作](/dotnet/framework/interop/index)