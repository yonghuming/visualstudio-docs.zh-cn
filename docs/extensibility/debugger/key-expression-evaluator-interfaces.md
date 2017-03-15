---
title: "键表达式计算器接口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，表达式计算"
  - "表达式计算、 接口"
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 键表达式计算器接口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 在编写时以及评估上下文的表达式计算器 \(EE\)，您应熟悉以下接口。  
  
## 界面说明  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     具有一个方法， [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), ，后者将获取一种数据结构，表示当前执行点。 这种数据结构是调试引擎 \(DE\) 将传递给三个参数之一 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 方法来计算表达式。 通常由符号提供程序实现此接口。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     具有 [将绑定](../../extensibility/debugger/reference/idebugbinder-bind.md) 方法，获取包含当前值的符号的内存区域。 提供这两个包含方法，由表示 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 对象和符号自身，由表示 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 对象， `IDebugBinder::Bind` 返回的符号值。`IDebugBinder` 通常由 DE 实现。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     表示一种简单的数据类型。 对于更复杂类型，如数组和方法，使用派生 [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) 和 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 接口，分别。[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 表示符号的另一个重要的派生的接口包含其他符号，如方法或类。`IDebugField` 界面 （以及其衍生产品） 通常由符号提供程序。  
  
     `IDebugField` 对象可用于查找的名称和类型的符号，并可在一起 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 对象，可以用来查找其值。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     表示一种符号的运行时值的实际位数。[将绑定](../../extensibility/debugger/reference/idebugbinder-bind.md) 采用 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 对象，它表示符号，并返回 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 对象。[GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) 方法返回的内存缓冲区中的符号值。 DE 通常实现此接口来表示内存中的属性的值。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     此接口表示表达式计算器本身。 主要方法是 [分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), ，它将返回 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 接口。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     此接口表示准备要进行求值的已分析的表达式。 主要方法是 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 后者表示值和类型的表达式将返回一个 IDebugProperty2。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     此接口表示一个值和其类型，并且是表达式计算的结果。  
  
## 请参阅  
 [评估上下文](../../extensibility/debugger/evaluation-context.md)