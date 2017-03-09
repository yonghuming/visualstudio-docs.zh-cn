---
title: "显示自定义数据类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat 文件"
  - "自定义数据类型"
  - "数据类型 [C#], 自定义"
  - "调试器, 扩展数据类型"
  - "托管代码, 自定义数据类型"
  - "mcee_cs.dat 文件"
  - "mcee_mc.dat 文件"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 显示自定义数据类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以在调试器变量窗口中自定义 Visual Studio 显示数据类型的方式。  
  
## 特性  
 在 C\# 和 Visual Basic 中，可以使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute> 和 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 来添加自定义数据的扩展。  
  
 在 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 代码中，Visual Basic 不支持 DebuggerBrowsable 特性。  此项限制在 .NET Framework 较高版本中已经删除。  
  
## 可视化工具  
 可以编写可视化工具来显示任何托管数据类型。  有关详细信息，请参阅[如何：编写可视化工具](../debugger/how-to-write-a-visualizer.md)。  
  
## 本机代码  
 对于本机代码，可以将自定义数据类型扩展添加到 autoexp.dat 文件中，该文件位于 Program Files\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger 目录中。  有关如何编写 `autoexp` 规则的说明就在该文件中。  
  
> [!CAUTION]
>  在 Visual Studio 的不同版本中，此文件的结构和 autoexp 规则的语法可能不同。  
  
 通过编写表达式计算器外接程序，还可以自定义本机类型视图。  有关详细信息，请参阅 [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/zh-cn/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)。  
  
## 请参阅  
 [使用 DebuggerTypeProxy 特性](../debugger/using-debuggertypeproxy-attribute.md)   
 [使用 DebuggerDisplay 特性](../debugger/using-the-debuggerdisplay-attribute.md)   
 [监视和快速监视窗口](../debugger/watch-and-quickwatch-windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)