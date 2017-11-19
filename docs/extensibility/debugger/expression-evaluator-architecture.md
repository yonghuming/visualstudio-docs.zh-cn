---
title: "表达式计算器体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6805b97da8e8f742b1b6c0bb3298e9324bb1f72e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluator-architecture"></a>表达式计算器体系结构
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 将专有语言集成到 Visual Studio 调试包是指实施所需的表达式计算器 (EE) 接口以及调用的公共语言运行时符号提供程序 (SP) 和联编程序接口。 SP 和联编程序的对象，以及当前的执行地址，是中的计算表达式的上下文。 这些接口生成和使用的信息表示 EE 的体系结构中的关键概念。  
  
## <a name="overview"></a>概述  
  
### <a name="parsing-the-expression"></a>分析表达式  
 调试程序时，有多种原因，但始终在已 （通过用户放置一个断点或一个引起的异常） 在断点处停止被调试的程序时计算的表达式。 所表示的是 Visual Studio 时获取堆栈帧，此时[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)接口，从 (DE) 的调试引擎。 然后调用 visual Studio [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)获取[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口。 此接口表示在其中可以计算表达式; 的上下文[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)是评估过程的入口点。 此点，直到由 DE 实现所有接口。  
  
 当`IDebugExpressionContext2::ParseText`是调用，DE 实例化与断点发生的位置的源代码文件的语言关联 EE （DE 还实例化 SH 此时）。 由表示 EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)接口。 然后调用 DE[分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)要转换为一个已分析表达式 （以文本形式） 的表达式，可供评估。 此分析的表达式由[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)接口。 请注意表达式通常分析并不会在此时评估。  
  
 DE 创建实现的对象[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口，将`IDebugParsedExpression`对象插入`IDebugExpression2`对象，并返回`IDebugExpression2`对象`IDebugExpressionContext2::ParseText`。  
  
### <a name="evaluating-the-expression"></a>计算表达式  
 Visual Studio 调用[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)已分析的表达式进行求值。 这两种方法调用[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync`调用的方法立即，而`IDebugExpression2::EvaluateAsync`调用通过后台线程的方法) 来计算已分析的表达式，并返回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示的值和分析的表达式类型的接口。 `IDebugParsedExpression::EvaluateSync`使用提供的 SH、 地址和联编程序将已分析的表达式转换为一个实际值，由表示`IDebugProperty2`接口。  
  
### <a name="for-example"></a>例如  
 在正在运行的程序命中断点后，用户选择查看中的变量**快速监视**对话框。 此对话框显示变量的名称、 其值和其类型。 通常，用户可以更改值。  
  
 当**快速监视**显示对话框、 检查变量的名称发送以文本形式向[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 这将返回[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)对象表示已分析的表达式中，在这种情况下，变量。 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)然后调用以生成`IDebugProperty2`表示变量的值和类型，以及其名称的对象。 它是将显示此信息。  
  
 如果用户更改变量的值， [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)调用使用新值，更改在内存中变量的值，以使程序恢复时，将使用它运行。  
  
 请参阅[显示局部变量](../../extensibility/debugger/displaying-locals.md)有关显示的变量的值的此过程的详细信息。 请参阅[更改的本地值](../../extensibility/debugger/changing-the-value-of-a-local.md)有关如何更改变量的值的详细信息。  
  
## <a name="in-this-section"></a>本节内容  
 [计算上下文](../../extensibility/debugger/evaluation-context.md)  
 提供当 DE 调用 EE 传递的参数。  
  
 [键表达式计算器接口](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 描述需要在编写 EE，以及评估上下文时的重要接口。  
  
## <a name="see-also"></a>另请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)   
 [更改局部值](../../extensibility/debugger/changing-the-value-of-a-local.md)