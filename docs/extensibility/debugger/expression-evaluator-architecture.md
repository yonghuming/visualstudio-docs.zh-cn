---
title: "表达式计算器体系结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "体系结构中，表达式计算器"
  - "表达式计算器，体系结构"
  - "调试 [调试 SDK]，表达式计算器"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 表达式计算器体系结构
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 将一种专有语言集成到 Visual Studio 调试程序包意味着实现所需的表达式计算器 \(EE\) 接口并调用公共语言运行时标符号提供程序 \(SP\) 和联编程序接口。 SP 对象和联编程序对象，以及当前的执行地址，在计算表达式的上下文。 这些接口生成和使用的信息表示 EE 体系结构中的关键概念。  
  
## 概述  
  
### 分析表达式  
 调试程序时，有多种原因，但始终当正在调试的程序已停止在断点处 （由用户放置一个断点或其中一个异常导致的异常） 计算的表达式。 由表示是在 Visual Studio 将获取一个堆栈帧，此时 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 接口，从调试引擎 \(DE\)。 Visual Studio 会再调用 [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 获取 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口。 此接口表示在其中可以计算表达式; 上下文 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 是评估过程的入口点。 到目前为止，为止的所有接口由 DE 都实现。  
  
 当 `IDebugExpressionContext2::ParseText` 是调用，DE 实例化 EE 与断点发生的位置的源代码文件的语言相关联 （DE 还实例化 SH 此时）。 由表示 EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) 接口。 然后调用 DE [分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 要转换为分析的表达式 （以文本形式） 的表达式，可供评估。 此分析的表达式都由 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 接口。 请注意表达式通常分析并不会在此时评估。  
  
 DE 创建一个对象，实现 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 接口，使 `IDebugParsedExpression` 对象插入 `IDebugExpression2` 对象，并返回 `IDebugExpression2` 对象从 `IDebugExpressionContext2::ParseText`。  
  
### 对表达式求值  
 Visual Studio 会调用任何一个 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 已分析的表达式进行求值。 这两种方法调用 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` 调用的方法，而 `IDebugExpression2::EvaluateAsync` 调用通过后台线程的方法\) 来计算分析的表达式并返回 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 表示的值和分析的表达式的类型的接口。`IDebugParsedExpression::EvaluateSync` 使用提供 SH、 地址和绑定器将分析的表达式转换为一个实际值，由 `IDebugProperty2` 接口。  
  
### 例如  
 在正在运行的程序命中断点后，用户选择要查看中的某个变量 **快速监视** 对话框。 此对话框中显示变量的名称、 其值和它的类型。 通常，用户可以更改值。  
  
 当 **快速监视** 显示对话框中，那么所检查的变量的名称发送以文本形式向 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 这将返回 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 对象，表示已分析的表达式中，在这种情况下，该变量。[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 然后调用以生成 `IDebugProperty2` 对象，表示变量的值和类型，以及它的名称。 这是将显示此信息。  
  
 如果用户更改变量的值， [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 用新值，更改在内存中变量的值，以使程序恢复时，将使用它调用运行。  
  
 请参阅 [显示局部变量](../../extensibility/debugger/displaying-locals.md) 有关显示变量的值的此过程的更多详细信息。 请参阅 [更改本地值](../../extensibility/debugger/changing-the-value-of-a-local.md) 有关如何更改变量的值的详细信息。  
  
## 本节内容  
 [评估上下文](../../extensibility/debugger/evaluation-context.md)  
 提供当 DE 调用 EE 传递的参数。  
  
 [键表达式计算器接口](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 描述需要编写 EE，以及评估上下文时的重要接口。  
  
## 请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)   
 [更改本地值](../../extensibility/debugger/changing-the-value-of-a-local.md)