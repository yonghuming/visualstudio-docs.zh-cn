---
title: "使用 DebuggerTypeProxy 特性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7796f11581f072e0437f341590bb064eeec81f7c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-debuggertypeproxy-attribute"></a>使用 DebuggerTypeProxy 特性
<xref:System.Diagnostics.DebuggerTypeProxyAttribute> 指定类型的代理或替身，并更改类型在调试器窗口中的显示方式。 查看具有代理的变量时，代理将代替原始类型出现在**显示**。 调试器变量窗口仅显示代理类型的公共成员。 不会显示私有成员。  
  
 此特性可应用于：  
  
-   结构  
  
-   类  
  
-   程序集  
  
 类型代理类必须具有一个构造函数，该函数采用代理将替换的类型的参数。 在每次需要显示目标类型的变量时，调试器都会创建类型代理类的一个新实例。 这会对性能产生一定影响。 因此，不应在构造函数中执行非必需的工作。  
  
 若要最大程度地减小性能损失，表达式计算器将不检查类型的显示代理上的特性，除非用户在调试器窗口中单击 + 符号或使用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 扩展该类型。 因此，不应将特性置于显示类型自身中。 特性可以且应该用于显示类型的正文中。  
  
 类型代理最好是作为特性目标类中的私有嵌套类。 这样，它便能轻松访问内部成员。  
  
 如果在程序集级别使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>，则 `Target` 参数将指定代理要替换的类型。  
  
 有关如何使用与此特性的示例<xref:System.Diagnostics.DebuggerDisplayAttribute>和<xref:System.Diagnostics.DebuggerTypeProxyAttribute>，请参阅[使用 DebuggerDisplay 特性](../debugger/using-the-debuggerdisplay-attribute.md)。  
  
## <a name="using-generics-with-debuggertypeproxy"></a>将泛型与 DebuggerTypeProxy 一起使用  
 对泛型的支持是有限的。 对于 C#，`DebuggerTypeProxy` 只支持开放类型。 开放类型（也称作“非构造类型”）是一种还未使用其类型参数的参数实例化的泛型类型。 不支持封闭类型（也称作“构造类型”）。  
  
 开放类型的语法类似于：  
  
 `Namespace.TypeName<,>`  
  
 如果使用泛型类型作为 `DebuggerTypeProxy` 中的目标，则必须使用该语法。 `DebuggerTypeProxy` 机制将为您推理类型参数。  
  
 在 C# 中的开放和封闭类型的详细信息请参阅[C# 语言规范](/dotnet/csharp/language-reference/language-specification)，20.5.2 节打开和关闭类型。  
  
 Visual Basic 没有开放类型语法，因此您无法在 Visual Basic 中执行同样的操作。 而必须使用开放类型名称的字符串表示形式。  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>另请参阅  
 [使用 DebuggerDisplay 特性](../debugger/using-the-debuggerdisplay-attribute.md)   
 [创建.managed 对象的自定义视图](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [使用调试器显示特性增强调试](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)