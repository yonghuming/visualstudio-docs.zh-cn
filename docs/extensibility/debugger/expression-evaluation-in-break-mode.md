---
title: "在中断模式下的表达式计算 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中断模式下，表达式计算"
  - "调试 [调试 SDK]，表达式计算"
  - "表达式计算、 中断模式"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 在中断模式下的表达式计算
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述发生的处理，调试器处于中断模式，并且必须执行表达式计算。  
  
## 表达式级别程序  
 这些是在计算表达式涉及的基本步骤:  
  
1.  会议调试管理器 \(SDM\)调用 [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 获取表达式上下文接口， [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。  
  
2.  SDM 然后调用与要分析的字符串的 [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 。  
  
3.  如果 ParseText 不返回 S\_OK，该错误的原因返回。  
  
     否则 \-  
  
     如果 ParseText 返回 S\_OK， SDM 然后可以调用 [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 从已分析的表达式的最后一个值。  
  
    -   对于使用 `IDebugExpression2::EvaluateSync`，特定回调接口用于将继续处理计算。  最终值在 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 接口返回。  
  
    -   对于使用 `IDebugExpression2::EvaluateAsync`，特定回调接口用于将继续处理计算。  一旦计算完成的， EvaluateAsync 通过回调发送一 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 接口。  此事件接口，最终值可以获取与 [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)