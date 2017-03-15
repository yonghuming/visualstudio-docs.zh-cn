---
title: "表达式计算 (Visual Studio 调试 SDK) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 68773ccac304972f4d96642a226a586d69efb783
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>表达式计算 (Visual Studio 调试 SDK)
在中断模式下，IDE 必须能够对涉及几个变量的程序的简单表达式求值。 若要实现此目的，调试引擎 (DE) 必须能够来分析和计算表达式，用于在 IDE 的窗口中的一个输入。  
  
 表达式在创建使用[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法和是否由生成表示[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口。  
  
 **IDebugExpression2**接口由 DE 并调用其**EvalAsync**方法以返回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) IDE 中，为了在 IDE 中显示表达式的计算结果的接口。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)返回一个可用于将表达式的值放到监视窗口或局部变量窗口的结构。  
  
 调试包或会话调试管理器 (SDM) 调用[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)获取[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)接口表示计算的结果。 `IDebugProperty2`具有名称、 类型和表达式的值返回的方法。 在不同的调试器窗口中显示此信息。  
  
## <a name="using-expression-evaluation"></a>使用表达式计算  
 若要使用表达式求值，则必须实现[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法及其所有的方法[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口，如下面的表中所示。  
  
|方法|说明|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以异步方式计算表达式。|  
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|结束异步表达式求值。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式计算表达式。|  
  
 同步和异步评估要求实现的[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 异步表达式计算都需要的实现[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>另请参阅  
 [执行控制和状态评估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
