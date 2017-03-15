---
title: "CA1901：P/Invoke 声明应为可移植声明 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1901：P/Invoke 声明应为可移植声明
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|类别|Microsoft.Portability|  
|是否重大更改|间断 \- 如果 P\/Invoke 在程序集外部可见。  无间断 \- 如果 P\/Invoke 在程序集外部不可见。|  
  
## 原因  
 此规则计算 P\/Invoke 的每个参数的大小和 P\/Invoke 的返回值，还验证它们在封送到 32 位和 64 位平台上的非托管代码时的大小是否正确。  与该规则最常见的冲突是，在需要与平台相关的指针大小的变量时，传递了固定大小的整数。  
  
## 规则说明  
 在以下任一情况下都会违反此规则：  
  
-   返回值或参数的类型为固定大小的整数，而实际类型应为 `IntPtr`。  
  
-   返回值或参数的类型为 `IntPtr`，而实际类型应为固定大小的整数。  
  
## 如何解决冲突  
 可通过使用 `IntPtr` 或 `UIntPtr`（而非 `Int32` 或 `UInt32`）表示句柄来修复此冲突。  
  
## 何时禁止显示警告  
 不应禁止显示此警告。  
  
## 示例  
 下面的示例演示与此规则的冲突。  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 在本示例中，`nIconIndex` 参数声明为 `IntPtr`是 4 个字节宽，宽 32 位平台上为 8 字节在 64 位平台。  在后面的非管理的声明中，您能够看到 `nIconIndex` 是所有平台上都有 4 位无符号整数。  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## 示例  
 若要修复此冲突，请将声明更改为以下内容：  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## 请参阅  
 [可移植性警告](../code-quality/portability-warnings.md)