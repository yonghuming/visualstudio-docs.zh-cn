---
title: "创建托管对象的自定义视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae3149350bac7aca92ffbc8b308c75357c3edba4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-views-of-managed-objects"></a>创建托管对象的自定义视图
可以在调试器变量窗口中自定义 Visual Studio 显示数据类型的方式。  
  
## <a name="attributes"></a>特性  
 在 C# 和 Visual Basic 中，可以使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute> 和 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 来添加自定义数据的扩展。  
  
 在 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 代码中，Visual Basic 不支持 DebuggerBrowsable 特性。 此项限制在 .NET Framework 较高版本中已经删除。  
  
## <a name="visualizers"></a>可视化工具  
 可以编写可视化工具来显示任何托管数据类型。 有关详细信息，请参阅[如何： 编写可视化工具](../debugger/how-to-write-a-visualizer.md)。  
  
## <a name="native-code"></a>本机代码  
 对于本机代码，可以将自定义数据类型扩展添加到 autoexp.dat 文件中，该文件位于 Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger 目录中。 有关如何编写 `autoexp` 规则的说明就在该文件中。  
  
> [!CAUTION]
>  在 Visual Studio 的不同版本中，此文件的结构和 autoexp 规则的语法可能不同。  
  
 通过编写表达式计算器外接程序，还可以自定义本机类型视图。 有关详细信息，请参阅[EEAddIn 示例： 调试表达式计算器外接程序](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 DebuggerTypeProxy 特性](../debugger/using-debuggertypeproxy-attribute.md)   
 [使用 DebuggerDisplay 特性](../debugger/using-the-debuggerdisplay-attribute.md)   
 [监视和快速监视窗口](../debugger/watch-and-quickwatch-windows.md)   
 [使用调试器显示特性增强调试](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)