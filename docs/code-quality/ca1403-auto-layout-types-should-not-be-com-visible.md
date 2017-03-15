---
title: "CA1403：自动布局类型不应对 COM 可见 | Microsoft Docs"
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
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403：自动布局类型不应对 COM 可见
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 通过将 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 特性设置为 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> 来标记组件对象模型 \(COM\) 可见的值类型。  
  
## 规则说明  
 <xref:System.Runtime.InteropServices.LayoutKind> 布局类型由公共语言运行时来管理。  这些类型的布局因 .NET Framework 的版本不同而不同，这将中断要求特定布局的 COM 客户端。  请注意，如果未指定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 特性，则 C\#、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 C\+\+ 编译器会为值类型指定 <xref:System.Runtime.InteropServices.LayoutKind> 布局。  
  
 除非另行标记，否则所有公共的非泛型类型都对 COM 可见；所有非公共类型和泛型类型都对 COM 不可见。  但是，为了减少误报，此规则要求显式声明类型的 COM 可见性；包含程序集必须用设置为 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 进行标记，类型必须用设置为 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 进行标记。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 特性的值更改为 <xref:System.Runtime.InteropServices.LayoutKind> 或 <xref:System.Runtime.InteropServices.LayoutKind>，或者使该类型对 COM 不可见。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型和一个满足该规则的类型。  
  
 [!CODE [FxCop.Interoperability.AutoLayout#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout#1)]  
  
## 相关规则  
 [CA1408：请不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## 请参阅  
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-cn/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [为互操作限定 .NET 类型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)