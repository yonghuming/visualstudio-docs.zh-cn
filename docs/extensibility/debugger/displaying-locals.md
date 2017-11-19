---
title: "显示局部变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a00d57b8af1c32c2f94334e2930e8f92b166c89b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-locals"></a>显示局部变量
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 始终执行的时间的方法，也称为包含的方法或当前方法的上下文中的位置。 时暂停执行，Visual Studio 会调用的调试引擎 (DE) 来获取本地变量的列表和自变量，统称为该方法的局部变量。 Visual Studio 将显示这些局部变量和中的值进行**局部变量**窗口。  
  
 若要显示局部变量，DE 调用[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)属于 EE 方法并为其指定评估上下文，即、 符号提供程序 (SP)，当前执行地址和联编程序对象。 有关详细信息，请参阅[评估上下文](../../extensibility/debugger/evaluation-context.md)。 如果调用成功，`IDebugExpressionEvaluator::GetMethodProperty`方法返回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)对象，用于表示包含当前执行地址的方法。  
  
 DE 调用[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)获取[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)对象，该筛选以返回唯一的局部变量和枚举可生成的一系列对象[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)结构。 每个结构包含名称、 类型和值的本地。 适用于显示的格式化字符串的形式存储的类型和值。 名称、 类型和值通常一起显示在某行中**局部变量**窗口。  
  
> [!NOTE]
>  **快速监视**和**监视**窗口还显示具有相同的格式的名称、 值和类型的变量。 但是，这些值通过调用中获取[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)而不是`IDebugProperty2::EnumChildren`。  
  
## <a name="in-this-section"></a>本节内容  
 [局部的实现示例](../../extensibility/debugger/sample-implementation-of-locals.md)  
 使用示例来单步执行实现局部变量的过程。  
  
## <a name="related-sections"></a>相关章节  
 [计算上下文](../../extensibility/debugger/evaluation-context.md)  
 说明当调试引擎 (DE) 调用表达式计算器 (EE) 时，它可以通过三个自变量。  
  
## <a name="see-also"></a>另请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)