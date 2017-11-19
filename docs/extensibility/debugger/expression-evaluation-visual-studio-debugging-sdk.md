---
title: "表达式计算 (Visual Studio 调试 SDK) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c66a6eac74b3d1494a1e98bcb95112c43c4c1bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>表达式计算 (Visual Studio 调试 SDK)
在中断模式下，IDE 必须能够计算涉及的程序的多个变量的简单表达式。 若要实现此目的，调试引擎 (DE) 必须能够分析和评估一 IDE 窗口中输入的表达式。  
  
 表达式在创建使用[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法和是否由生成表示[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口。  
  
 **IDebugExpression2**接口由 DE 和调用实现其**EvalAsync**方法以返回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)到 IDE 中，为了显示接口在 IDE 中的表达式计算的结果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)返回可用于将表达式的值放到监视窗口或局部变量窗口的结构。  
  
 调试包或会话调试管理器 (SDM) 调用[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)获取[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示的接口计算的结果。 `IDebugProperty2`具有返回名称、 类型和表达式的值的方法。 此信息显示在不同的调试器窗口中。  
  
## <a name="using-expression-evaluation"></a>使用表达式计算  
 若要使用表达式计算，则必须实现[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法及其所有的方法[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口下, 表中所示。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以异步方式计算表达式。|  
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|结束异步表达式计算。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式计算表达式。|  
  
 同步和异步评估要求实现[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 异步表达式计算需要实现[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>另请参阅  
 [执行控件和状态计算](../../extensibility/debugger/execution-control-and-state-evaluation.md)