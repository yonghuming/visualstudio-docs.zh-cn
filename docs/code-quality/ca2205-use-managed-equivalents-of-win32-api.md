---
title: "CA2205：使用 Win32 API 的托管等效项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2205：使用 Win32 API 的托管等效项
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 定义了平台调用方法，但在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类库中存在具有等效功能的方法。  
  
## 规则说明  
 平台调用方法用于调用非托管 DLL 函数，该方法使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 特性（在 Visual Basic 中使用 `Declare` 关键字）进行定义。  如果平台调用方法定义不正确，则可能会因错误命名的函数、错误的参数映射和返回值类型、错误的字段说明（如调用约定和字符集）等问题导致运行时异常。  如果存在等效托管方法，则调用等效托管方法通常要比直接定义和调用非托管方法简单的多，并且也不容易发生错误。  调用平台调用方法还会导致其他需要解决的安全问题。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使用对非托管函数的托管等效项的调用来代替对非托管函数的调用。  
  
## 何时禁止显示警告  
 如果建议的替代方法无法提供所需的功能，则可以禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的平台调用方法定义。  此外，还演示了对该平台调用方法及等效托管方法的调用。  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## 相关规则  
 [CA1404：紧接在 P\/Invoke 之后调用 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060：将 P\/Invoke 移动到 NativeMethods 类](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400：P\/Invoke 入口点应该存在](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401：P\/Invokes 应该是不可见的](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101：指定对 P\/Invoke 字符串参数进行封送处理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)