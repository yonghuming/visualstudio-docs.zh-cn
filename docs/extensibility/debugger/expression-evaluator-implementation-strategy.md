---
title: "表达式计算器实现策略 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40b97c53570362c79bf3b1627ad183dcf6964b9c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluator-implementation-strategy"></a>表达式计算器实现策略
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 快速创建的表达式计算器 (EE) 的一种方法是首先实现显示中的局部变量所必需的最小代码**局部变量**窗口。 最好请注意，中的每一行**局部变量**窗口显示名称、 类型和本地变量的值，并由表示所有三个[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)对象。 名称、 类型和本地变量的值可以从获取`IDebugProperty2`对象通过调用其[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 有关如何显示中的本地变量的详细信息**局部变量**窗口中，请参阅[显示局部变量](../../extensibility/debugger/displaying-locals.md)。  
  
## <a name="discussion"></a>讨论  
 可能的实现序列开头实现[IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)。 [分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)和[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)方法需要实施要显示局部变量。 调用`IDebugExpressionEvaluator::GetMethodProperty`返回`IDebugProperty2`对象，表示的方法： 即[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)对象。 方法本身不会显示在**局部变量**窗口。  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)应下一步实现方法。 调试引擎 (DE) 调用此方法来获取本地变量和自变量的列表传递`IDebugProperty2::EnumChildren``guidFilter`参数`guidFilterLocalsPlusArgs`。 `IDebugProperty2::EnumChildren`调用[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)和[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)，结合单个枚举中的结果。 请参阅[显示局部变量](../../extensibility/debugger/displaying-locals.md)有关详细信息。  
  
## <a name="see-also"></a>另请参阅  
 [实现表达式计算器](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [显示局部](../../extensibility/debugger/displaying-locals.md)