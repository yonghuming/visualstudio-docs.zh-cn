---
title: "显示局部变量 | Microsoft Docs"
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
  - "表达式计算、 显示局部变量"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 显示局部变量
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 始终执行方法，也称为含有方法或当前方法的上下文内发生。 暂停执行，Visual Studio 会调用的调试引擎 \(DE\) 来获取本地变量的列表和参数，统称为该方法的局部变量。 Visual Studio 将显示这些局部变量和中的值进行 **局部变量** 窗口。  
  
 若要显示局部变量，DE 调用 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 属于 EE 方法并为其提供评估上下文，即、 符号提供程序 \(SP\)、 当前执行地址和联编程序对象。 有关更多信息，请参见[评估上下文](../../extensibility/debugger/evaluation-context.md)。 如果调用成功， `IDebugExpressionEvaluator::GetMethodProperty` 方法将返回 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 对象，表示包含当前执行地址的方法。  
  
 DE 调用 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 获取 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 对象，该筛选，以返回唯一的局部变量和枚举以生成的列表对象 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 结构。 每个结构包含名称、 类型和一个本地值。 类型和值以适合显示的格式化字符串形式存储。 名称、 类型和值通常一起显示在一行中 **局部变量** 窗口。  
  
> [!NOTE]
>  **快速监视** 和 **监视** 窗口还显示具有相同的格式的名称、 值和类型的变量。 但是，这些值通过调用中获取 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 而不是 `IDebugProperty2::EnumChildren`。  
  
## 本节内容  
 [局部变量的实现示例](../../extensibility/debugger/sample-implementation-of-locals.md)  
 使用示例来单步执行实现局部变量的过程。  
  
## 相关章节  
 [评估上下文](../../extensibility/debugger/evaluation-context.md)  
 说明当调试引擎 \(DE\) 调用表达式计算器 \(EE\) 时，它可以通过三个参数。  
  
## 请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)