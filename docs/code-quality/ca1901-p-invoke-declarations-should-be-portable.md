---
title: "CA1901: P Invoke 声明应为可移植 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3c048ae73e2b15035c9be8afd6a82c860544bb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901：P/Invoke 声明应为可移植声明
|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|类别|Microsoft.Portability|  
|是否重大更改|是-如果 P/Invoke 集外可见。 非重大更改-如果 P/Invoke 不是程序集外部可见。|  
  
## <a name="cause"></a>原因  
 此规则计算 P/Invoke 的返回值和每个参数的大小，并验证其大小，当封送到非托管代码在 32 位和 64 位平台上，验证正确。 与此规则的最常见的冲突是将固定大小整数传递要求取决于平台，指针大小的变量的位置。  
  
## <a name="rule-description"></a>规则说明  
 下列任一情况下与该规则冲突发生：  
  
-   返回值或参数的类型为固定大小整数类型应为`IntPtr`。  
  
-   返回值或参数被类型化为`IntPtr`时它的类型应为固定大小的整数。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 你可以通过使用来解决此冲突`IntPtr`或`UIntPtr`表示句柄而不是`Int32`或`UInt32`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不应禁止显示此警告。  
  
## <a name="example"></a>示例  
 下面的示例演示此规则的冲突。  
  
```csharp  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 在此示例中，`nIconIndex`参数声明为`IntPtr`，即宽 32 位平台和 8 个字节宽在 64 位平台上的 4 个字节。 在非托管声明中后面，你可以看到，`nIconIndex`是在所有平台上的 4 字节无符号的整数。  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>示例  
 若要解决冲突，请将声明更改为以下：  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Portability Warnings](../code-quality/portability-warnings.md)