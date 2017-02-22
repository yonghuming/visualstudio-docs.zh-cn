---
title: "监视窗口表达式求值 | Microsoft Docs"
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
  - "监视窗口表达式"
  - "监视窗口中表达式"
  - "表达式计算、 监视窗口表达式"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 监视窗口表达式求值
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 当暂停执行时，Visual Studio 会调用调试引擎 \(DE\) 以确定其监视列表中的每个表达式的当前值。 DE 每个使用计算表达式的表达式计算器 \(EE\) 和 Visual Studio 将显示在其值 **监视** 窗口。  
  
 下面是概述如何评估监视列表表达式:  
  
1.  Visual Studio 会调用 DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 以获取可用于对表达式求值表达式上下文。  
  
2.  对于监视列表中的每个表达式，Visual Studio 会调用 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 将表达式文本转换为分析的表达式。  
  
3.  `IDebugExpressionContext2::ParseText` 调用 [分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 若要执行的分析的文本和产生的实际工作 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 对象。  
  
4.  `IDebugExpressionContext2::ParseText` 创建 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 对象，并将 `IDebugParsedExpression` 到其中的对象。 此我`DebugExpression2` 对象然后返回到 Visual Studio。  
  
5.  Visual Studio 调用 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 已分析的表达式进行求值。  
  
6.  `IDebugExpression2::EvaluateSync` 将传递到调用 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 以执行实际的计算，从而生成 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 返回到 Visual Studio 的对象。  
  
7.  Visual Studio 调用 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 来获取随后观察列表中会显示该表达式的值。  
  
## 分析，然后评估  
 分析复杂表达式可能需要更长时间对其进行评估，因为表达式的计算过程将分解为两个步骤: 1\) 分析表达式和 2\) 评估分析的表达式。 这样一来，评估可发生多次，但需要一次分析该表达式。 从在 EE 返回中间分析的表达式 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 对象，进而封装并从作为 DE 返回 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 对象。`IDebugExpression` 对象将所有计算交都由 `IDebugParsedExpression` 对象。  
  
> [!NOTE]
>  没有必要 EE 遵守此两步过程，即使 Visual Studio 假定该问题;EE 可以分析和评估在相同的步骤时 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 称为 \(这是 MyCEE 示例的工作方式，例如\)。 如果您的语言可以构成复杂的表达式，您可能想要分析步骤分开评估步骤。 这可以提高在 Visual Studio 调试器中的性能，当许多监视表达式正在显示。  
  
## 本节内容  
 [表达式计算的实现示例](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 使用 MyCEE 示例逐步执行表达式计算过程。  
  
 [评估监视表达式](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 介绍了成功表达式分析后发生的情况。  
  
## 相关章节  
 [评估上下文](../../extensibility/debugger/evaluation-context.md)  
 提供的调试引擎 \(DE\) 调用表达式计算器 \(EE\) 时传递的参数。  
  
## 请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)