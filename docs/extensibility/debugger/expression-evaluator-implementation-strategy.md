---
title: "表达式计算器实施策略 | Microsoft Docs"
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
  - "表达式计算、 实施策略"
  - "调试引擎，实施策略"
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 表达式计算器实施策略
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 快速创建的表达式计算器 \(EE\) 的一种方法是首先实现显示中的局部变量所需的最小代码 **局部变量** 窗口。 它可要认识到，中的每一行 **局部变量** 窗口显示名称、 类型和值的局部变量，并由表示所有这三 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 对象。 名称、 类型和本地变量的值可从 `IDebugProperty2` 对象通过调用其 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法。 有关如何显示中的局部变量 **局部变量** 窗口中，请参阅 [显示局部变量](../../extensibility/debugger/displaying-locals.md)。  
  
## 讨论  
 可能的实现顺序从开始实现 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)。[分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 和 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 方法需要实施要显示局部变量。 调用 `IDebugExpressionEvaluator::GetMethodProperty` 返回 `IDebugProperty2` 对象，表示一种方法︰ 即 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 对象。 方法本身不会显示在 **局部变量** 窗口。  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 应下一步实现方法。 调试引擎 \(DE\) 调用此方法来获取本地变量和参数的列表传递 `IDebugProperty2::EnumChildren``guidFilter` 参数 `guidFilterLocalsPlusArgs`。`IDebugProperty2::EnumChildren` 调用 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 和 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), ，组合中的一个枚举的结果。 有关详细信息，请参见 [显示局部变量](../../extensibility/debugger/displaying-locals.md)。  
  
## 请参阅  
 [实现表达式计算器](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)