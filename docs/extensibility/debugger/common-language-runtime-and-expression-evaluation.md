---
title: "公共语言运行时和表达式计算 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba9a9a6b406ad5a94cced7820e6b4581db56eb2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="common-language-runtime-and-expression-evaluation"></a>公共语言运行时和表达式计算
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 编译器，如 Visual Basic 和 C# （读作 c-sharp），面向公共语言运行时 (CLR)，生成 Microsoft 中间语言 (MSIL)，这是更高版本编译为本机代码。 CLR 提供调试引擎 (DE) 生成的代码进行调试。 如果你打算将专有的编程语言集成到 Visual Studio IDE，你可以选择编译为 MSIL 并因此不需要编写你自己 DE。 但是，你将需要编写能够计算表达式的上下文中的编程语言的表达式计算器 (EE)。  
  
## <a name="discussion"></a>讨论  
 通常，分析计算机语言表达式，以生成一组数据对象和一组用于对其进行处理的运算符。 例如，"A + B"可能分析将加法运算符 （+） 的数据的表达式的对象"A"和"B，"可能会导致另一个数据对象。 总的一套数据对象、 运算符和它们的关联通常在程序中表示为一个树，并在该树的节点的运算符和分支上的数据对象。 已分解为树的形式的表达式通常称为已分析的树。  
  
 一旦已分析表达式，被调用符号提供程序 (SP) 来计算每个数据对象。 例如，如果同时在多个方法，则这一问题定义"A"，则"哪些 A？" 可以确定 A 的值之前必须回答。 返回 SP 问题的回答是类似于"第五个堆栈帧上第三个项"或者"是 50 个字节，超出的静态内存开始一个分配给此方法。"  
  
 除了为程序本身生成 MSIL，CLR 编译器还可以生成很具有说明性写入到程序数据库 (.pdb) 文件的调试信息。 只要专有语言编译器生成调试信息放在与 CLR 编译器相同的格式，CLR 的 SP 是无法识别的语言的名为数据对象。 一旦已确定的已命名的数据对象，EE 使用联编程序对象关联 （或绑定） 的数据对象到的内存区域中保留该对象的值。 然后，DE 可以获取或设置数据对象的新值。  
  
 专有编译器可以提供通过调用调试信息的 CLR`ISymbolWriter`接口 (命名空间中的.NET Framework 中定义`System.Diagnostics.SymbolStore`)。 通过编译为 MSIL 并编写通过这些接口的调试信息、 专有编译器可以使用 CLR DE 和 sp。 这极大地简化了将专有语言集成到 Visual Studio IDE。  
  
 当 CLR DE 调用专有的 EE 计算的表达式时，DE 提供 EE 具有 SP 和联编程序对象的接口。 因此，编写基于 CLR 的调试引擎意味着它只有才需要实现适当的表达式计算器接口;CLR 将负责的绑定和为你处理的符号。  
  
## <a name="see-also"></a>另请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)