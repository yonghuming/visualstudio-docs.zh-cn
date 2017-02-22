---
title: "CA1404：紧接在 P/Invoke 之后调用 GetLastError | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1404：紧接在 P/Invoke 之后调用 GetLastError
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|类别|Microsoft.Interoperability|  
|是否重大更改|非重大更改|  
  
## 原因  
 调用了 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> 方法或等效的 Win32 `GetLastError` 函数，并且紧邻的前一个调用并非针对平台调用方法。  
  
## 规则说明  
 平台调用方法访问非托管代码，而且是使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Declare` 关键字或使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 特性定义的。  发生失败时，非托管函数通常会调用 Win32 `SetLastError` 函数，以便设置与失败关联的错误代码。  发生失败的函数的调用方调用 Win32 `GetLastError` 函数，以检索错误代码并确定失败的原因。  错误代码按线程维护，并且被对 `SetLastError` 的下一次调用覆盖。  调用失败的平台调用方法后，托管代码可以通过调用 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法检索错误代码。  因为错误代码可以被其他托管类库方法的内部调用覆盖，所以在调用平台调用方法后应立即调用 `GetLastError` 或 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法。  
  
 当在对平台调用方法的调用和对 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 的调用之间出现以下托管成员时，该规则将忽略对它们的调用。  这些成员不更改错误代码，这对于确定某些对平台调用方法的调用是否成功非常有用。  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## 如何解决冲突  
 要修复与该规则的冲突，请移动对 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 的调用，使它紧跟在对平台调用方法的调用之后。  
  
## 何时禁止显示警告  
 如果平台调用方法调用和 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法调用之间的代码不能显式或隐式地更改错误代码，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的方法和一个满足该规则的方法。  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## 相关规则  
 [CA1060：将 P\/Invoke 移动到 NativeMethods 类](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400：P\/Invoke 入口点应该存在](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401：P\/Invokes 应该是不可见的](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101：指定对 P\/Invoke 字符串参数进行封送处理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205：使用 Win32 API 的托管等效项](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)