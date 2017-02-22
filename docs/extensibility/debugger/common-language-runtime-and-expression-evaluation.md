---
title: "公共语言运行时和表达式计算 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，表达式计算"
  - "表达式计算、 和公共语言运行时"
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 公共语言运行时和表达式计算
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 编译器中，如 Visual Basic 和 C\# （读作 c\-sharp），面向公共语言运行时 \(CLR\)，生成 Microsoft 中间语言 \(MSIL\)，这是更高版本编译为本机代码。 CLR 提供的调试引擎 \(DE\) 生成的代码进行调试。 如果您打算将您专有的编程语言集成到 Visual Studio IDE，您可以选择将编译为 MSIL 并因此将不需要编写您自己 DE。 但是，您将必须编写的表达式计算器 \(EE\) 能够计算表达式的上下文中的编程语言。  
  
## 讨论  
 通常，分析计算机的语言表达式，以产生一组数据对象和一组用来对其进行处理的运算符。 例如，"A \+ B"可能会对分析，以应用加法运算符 （\+） 对数据的表达式的对象"A"和"B"甚至可能会导致另一个数据对象。 总的数据对象、 运算符和它们的关联集最常用程序中表示为一个树，并在该树的节点的运算符和分支办公室的数据对象。 已分解为树的形式的表达式通常称为经过分析的树。  
  
 一旦已分析表达式，被调用符号提供程序 \(SP\) 来计算每个数据对象。 例如，如果同时在多个方法，则问题定义"A"，则"哪个 A？" 可以确定 A 的值之前必须回答。 返回由 SP 的答案是类似于"第五个堆栈帧上的第三项"或者"是 50 个字节，超出的静态内存开始一个分配给此方法。"  
  
 除了为程序本身生成 MSIL，CLR 编译器还可以生成很具有说明性写入到程序数据库 \(.pdb\) 文件的调试信息。 只要专有语言编译器生成调试信息放在与 CLR 编译器相同的格式，CLR 的 SP 是能够将标识语言的名为数据对象。 一旦确定已命名的数据对象，EE 使用联编程序对象以将相关联 （或绑定） 的数据对象到包含该对象的值的内存区域。 然后，DE 可以获取或设置数据对象的新值。  
  
 专有编译器可以提供 CLR 调试信息通过调用 `ISymbolWriter` 接口 \(其中定义命名空间中的.NET Framework 中 `System.Diagnostics.SymbolStore`\)。 专有编译器可以通过编译为 MSIL 并编写调试信息通过这些接口，使用 CLR DE 和 sp。 这极大地简化了将专有语言集成到 Visual Studio IDE。  
  
 当 CLR DE 调用专有 EE 计算的表达式时，DE 提供 EE 带有 SP 和联编程序对象的接口。 因此，编写基于 CLR 的调试引擎意味着很有必要仅实现适当的表达式计算器接口;CLR 负责为您处理的符号和绑定。  
  
## 请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)