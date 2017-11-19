---
title: "在中断模式下的表达式计算 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 766f00475971da1ca009737f9360952422177814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-in-break-mode"></a>在中断模式下的表达式计算
下面描述了当调试器处于中断模式，并且必须执行表达式计算时出现的过程。  
  
## <a name="expression-evaluation-process"></a>表达式评估过程  
 以下是所涉及的表达式进行求值的基本步骤：  
  
1.  会话调试管理器 (SDM) 调用[IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)获取表达式上下文接口， [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。  
  
2.  然后调用 SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)与要分析的字符串。  
  
3.  如果 ParseText 不返回，则为 S_OK，则返回错误的原因。  
  
     -否则为-  
  
     如果 ParseText 不返回，则为 S_OK，SDM 可以然后调用[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)以获取从已分析的表达式的一个最终值。  
  
    -   对于使用`IDebugExpression2::EvaluateSync`，给定的回调接口用于通信的评估的持续过程。 在中返回的最终值[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)接口。  
  
    -   对于使用`IDebugExpression2::EvaluateAsync`，给定的回调接口用于通信的评估的持续过程。 完成评估后，将发送 EvaluateAsync [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)通过回调接口。 与此事件界面的最终值可以获取与[GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)。  
  
## <a name="see-also"></a>另请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)