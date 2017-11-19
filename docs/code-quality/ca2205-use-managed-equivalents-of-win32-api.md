---
title: "CA2205： 使用托管的 Win32 API 的等效项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cbdc02843d0a2982a129dafd5948a4c1ab287427
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205：使用 Win32 API 的托管等效项
|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 平台调用定义方法和具有等效功能的方法中存在[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]类库。  
  
## <a name="rule-description"></a>规则说明  
 平台调用方法可用于调用非托管的 DLL 函数，并使用定义<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性，或`Declare`在 Visual Basic 中的关键字。 定义不正确的平台调用方法可能会导致运行时异常由于问题，如错误命名的函数，发生故障的参数和返回值数据类型和不正确的字段规范，如的调用约定和字符映射设置。 如果可用，但它通常是更简单且小于错误倾向于调用比定义并直接调用非托管的方法等效的托管的方法。 调用平台调用方法也会导致需解决此问题的其他安全问题。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请将对非托管函数的调用替换为其等效的托管的调用。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果建议的替代方法未提供所需的功能，禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 以下示例显示了一个平台调用方法定义与该规则冲突。 此外，对平台调用调用方法，并显示等效的托管的方法。  
  
 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1404： 紧接在 P/Invoke 之后调用 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060： 将 P/Invoke 到 NativeMethods 类](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P/Invoke 入口点应该存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes 应该是不可见](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101： 指定对 P/Invoke 字符串自变量封送处理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)