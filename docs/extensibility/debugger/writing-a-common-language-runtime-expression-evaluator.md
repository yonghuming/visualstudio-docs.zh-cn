---
title: "编写公共语言运行时表达式计算器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "表达式计算器教程"
  - "表达式计算、 示例"
  - "调试 [调试 SDK]，表达式计算器教程"
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 编写公共语言运行时表达式计算器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表达式计算器 \(EE\) 是调试引擎 \(DE\) 处理该语法的一部分和生成正在调试的代码的编程语言的语义。 一种编程语言的上下文中，必须对表达式进行计算。 例如，在某些语言中，"A \+ B"的表达式表示"之和 A 和 b。" 在其他语言中，同一表达式可能表示"A 或 b." 因此，单独 EE 必须可用于在 Visual Studio IDE 中生成对象代码要调试每种编程语言。  
  
 Visual Studio 调试包的某些方面必须解释的编程语言的上下文中的代码。 例如，执行停止在断点处，键入用户具有的任意表达式 **监视** 必须计算并显示窗口。 此外，用户可以更改本地变量的值，通过键入一个表达式到 **监视** 窗口或 **即时** 窗口。  
  
## 本节内容  
 [公共语言运行时和表达式计算](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 说明: 当你要集成到 Visual Studio IDE 的专有的编程语言，编写 EE 能够计算表达式的上下文中的专有语言允许您编译为 Microsoft 中间语言 \(MSIL\)，而无需编写调试引擎。  
  
 [表达式计算器体系结构](../../extensibility/debugger/expression-evaluator-architecture.md)  
 讨论如何实现所需的 EE 接口并调用公共语言运行时符号提供程序 \(SP\) 和联编程序接口。  
  
 [注册的表达式计算器](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 说明 EE 必须将自身注册为公共语言运行时和 Visual Studio 运行时环境的类工厂。  
  
 [实现表达式计算器](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 介绍如何评估表达式的过程包含调试引擎 \(DE\)、 符号提供程序 \(SP\)、 联编程序对象和表达式计算器 \(EE\)。  
  
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)  
 描述如何操作，请时暂停执行，调试程序包会调用 DE 来获取本地变量和参数列表。  
  
 [监视窗口表达式求值](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 介绍 Visual Studio 调试包调用 DE 以确定其监视列表中的每个表达式的当前值的方式。  
  
 [更改本地值](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 说明，更改本地的值，在局部变量窗口每一行都具有一个关联的对象，提供名称、 类型和当前值的本地。  
  
 [实现自定义查看器以及类型的可视化工具](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 说明哪些接口必须由哪个组件以支持类型的可视化工具和自定义查看器来实现。  
  
## 请参阅  
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)