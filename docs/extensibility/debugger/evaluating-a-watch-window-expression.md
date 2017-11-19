---
title: "监视窗口表达式求值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03a74bf73f457009a6f17f8e7bdda8e4e7b9e35f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="evaluating-a-watch-window-expression"></a>监视窗口表达式求值
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 当将暂停执行时，Visual Studio 会调用的调试引擎 (DE) 以确定其监视列表中每个表达式的当前值。 DE 每个使用计算表达式的表达式计算器 (EE) 和 Visual Studio 将显示在其值**监视**窗口。  
  
 下面是概述如何评估监视列表表达式：  
  
1.  Visual Studio 会调用 DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)以获取可以用于对表达式求值表达式上下文。  
  
2.  监视列表中每个表达式，Visual Studio 会调用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)将表达式文本转换为一个已分析的表达式。  
  
3.  `IDebugExpressionContext2::ParseText`调用[分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)来执行的分析的文本和生成的实际工作[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)对象。  
  
4.  `IDebugExpressionContext2::ParseText`创建[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)对象并将`IDebugParsedExpression`到其中的对象。 此我`DebugExpression2`对象然后返回到 Visual Studio。  
  
5.  Visual Studio 调用[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)已分析的表达式进行求值。  
  
6.  `IDebugExpression2::EvaluateSync`将传递到调用[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)执行实际评估并生成[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)返回到 Visual Studio 的对象。  
  
7.  Visual Studio 调用[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)以获取然后监视列表中显示的表达式的值。  
  
## <a name="parse-then-evaluate"></a>分析，然后评估  
 由于分析的复杂表达式可能需要更长时间对其进行评估，表达式的计算过程将分解为两个步骤： 1） 分析表达式和 2） 计算已分析的表达式。 这样一来，评估可发生多次，但需要一次分析该表达式。 从 EE 中返回的中间的已分析的表达式[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)对象，反过来封装并返回从作为 DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)对象。 `IDebugExpression`对象将所有计算交都由`IDebugParsedExpression`对象。  
  
> [!NOTE]
>  没有必要 EE 为遵守此两步过程，即使 Visual Studio 假定该问题;EE 可以分析和评估在同一步骤时[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)称为 （这是 MyCEE 示例的工作方式，例如）。 如果你的语言可以构成复杂表达式，你可能想要评估步骤中分隔分析步骤。 这可以提高在 Visual Studio 调试器中的性能，当许多监视表达式正在显示。  
  
## <a name="in-this-section"></a>本节内容  
 [表达式计算的实现示例](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 使用 MyCEE 示例来单步执行的表达式计算过程。  
  
 [计算监视表达式](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 说明成功表达式分析后进行什么操作。  
  
## <a name="related-sections"></a>相关章节  
 [计算上下文](../../extensibility/debugger/evaluation-context.md)  
 提供的调试引擎 (DE) 调用表达式计算器 (EE) 时传递的参数。  
  
## <a name="see-also"></a>另请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)