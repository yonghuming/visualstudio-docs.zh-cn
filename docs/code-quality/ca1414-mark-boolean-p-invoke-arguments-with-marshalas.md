---
title: "CA1414：用 MarshalAs 标记布尔型 P/Invoke 参数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414：用 MarshalAs 标记布尔型 P/Invoke 参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 平台调用方法声明包括一个 <xref:System.Boolean?displayProperty=fullName> 参数或返回值，但是未将 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> 特性应用于该参数或返回值。  
  
## 规则说明  
 平台调用方法访问非托管代码，而且是使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Declare` 关键字或使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 定义的。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> 指定用于在托管代码与非托管代码之间转换数据类型的封送处理行为。  许多简单数据类型（如 <xref:System.Byte?displayProperty=fullName> 和 <xref:System.Int32?displayProperty=fullName>）在托管代码中都只有一种表示形式，无需为它们指定封送处理行为；公共语言运行时会自动提供正确的行为。  
  
 <xref:System.Boolean> 数据类型在非托管代码中有多种表示形式。  当未指定 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 时，<xref:System.Boolean> 数据类型的默认封送处理行为是 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。  这是 32 位整数，并不适用于所有情况。  应当确定非托管方法所需的布尔表示形式并将其与相应的 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> 匹配。  UnmanagedType.Bool 是 Win32 BOOL 类型，它总是为 4 个字节。  UnmanagedType.U1 应当用于 C\+\+ `bool` 或其他单字节类型。  有关更多信息，请参见 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/zh-cn/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 应用于 <xref:System.Boolean> 参数或返回值。  将该特性的值设置为相应的 <xref:System.Runtime.InteropServices.UnmanagedType>。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  显式指定此行为会使代码更易于维护，即使默认封送处理行为适用也是如此。  
  
## 示例  
 下面的示例演示两个标记有相应 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性的平台调用方法。  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## 相关规则  
 [CA1901：P\/Invoke 声明应为可移植声明](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101：指定对 P\/Invoke 字符串参数进行封送处理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/zh-cn/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)