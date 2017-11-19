---
title: "CA1404： 紧接在 P Invoke 之后调用 GetLastError |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 63cd84136861b80617285a5f7f03ff4767efddca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404：紧接在 P/Invoke 之后调用 GetLastError
|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|类别|Microsoft.Interoperability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 调用了<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>方法或等效的 Win32`GetLastError`函数，并且紧邻的前调用不为平台调用方法。  
  
## <a name="rule-description"></a>规则说明  
 平台调用方法访问非托管的代码，而且使用定义`Declare`中的关键字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性。 通常情况下，在失败的非托管的函数调用 Win32`SetLastError`函数可设置与错误相关联的错误代码。 失败的函数的调用方调用 Win32`GetLastError`函数以检索错误代码并确定失败的原因。 错误代码的每个线程基础上维护和的后续调用会覆盖`SetLastError`。 托管的代码的调用失败的平台调用方法后，可以通过调用检索错误代码<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法。 因为从其他托管的类库方法，内部调用可以覆盖错误代码`GetLastError`或<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>的平台调用方法调用后立即应该调用方法。  
  
 规则将忽略对以下调用托管的成员对平台调用之间发生时调用方法和调用<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>。 这些成员未更改的错误代码，并可用于确定某个平台的成功调用的方法调用。  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将调用移到<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>，以便它立即跟随到平台调用调用方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果该平台之间的代码调用方法调用和<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法调用不显式或隐式会导致更改的错误代码。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的方法以及满足该规则的方法。  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1060： 将 P/Invoke 到 NativeMethods 类](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P/Invoke 入口点应该存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes 应该是不可见](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101： 指定对 P/Invoke 字符串自变量封送处理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205：使用 Win32 API 的托管等效项](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)