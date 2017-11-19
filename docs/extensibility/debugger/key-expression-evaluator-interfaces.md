---
title: "键表达式计算器接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a03d419122f3cb72b3b9573279b41bc0de2636c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="key-expression-evaluator-interfaces"></a>键表达式计算器接口
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 在编写时以及评估上下文的表达式计算器 (EE)，你应该熟悉以下接口。  
  
## <a name="interface-descriptions"></a>界面说明  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     具有一个方法， [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)，后者将获取一种数据结构，表示当前执行点。 此数据结构是调试引擎 (DE) 将传递给的三个自变量之一[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)方法来计算表达式。 此接口通常是由符号提供程序实现的。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     具有[绑定](../../extensibility/debugger/reference/idebugbinder-bind.md)方法，获取包含符号的当前值的内存区域。 给定两个包含，所表示的方法[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)对象，并且符号自身，由表示[IDebugField](../../extensibility/debugger/reference/idebugfield.md)对象，`IDebugBinder::Bind`返回的符号值。 `IDebugBinder`通常由 DE 实现。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     表示一种简单的数据类型。 对于更复杂的类型，如数组和方法，使用派生[IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md)和[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)接口，分别。 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)是另一个重要的派生的接口，表示包含其他符号，如方法或类的符号。 `IDebugField`符号提供程序接口 （和其衍生产品） 通常实现。  
  
     `IDebugField`对象可以是用于查找的名称和类型的符号，并且可在与它们一起[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)对象，可用于查找其值。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     表示符号的运行时间值的实际位。 [将绑定](../../extensibility/debugger/reference/idebugbinder-bind.md)采用[IDebugField](../../extensibility/debugger/reference/idebugfield.md)对象，它表示一个符号，并返回[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)对象。 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md)方法内存缓冲区中返回的符号值。 DE 通常实现此接口来表示内存中的属性的值。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     此接口表示表达式计算器本身。 关键的方法是[分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)，它将返回[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)接口。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     此接口表示准备要进行求值的已分析的表达式。 关键的方法是[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)后者表示的值和类型的表达式将返回一个 IDebugProperty2。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     此接口表示一个值和其类型，是表达式计算的结果。  
  
## <a name="see-also"></a>另请参阅  
 [计算上下文](../../extensibility/debugger/evaluation-context.md)