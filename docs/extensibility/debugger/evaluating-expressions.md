---
title: "计算表达式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "计算表达式 [调试 SDK]"
  - "调试 [调试 SDK]，表达式计算"
  - "表达式计算"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 计算表达式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

表达式从汽车、 "、 " 或 " 即时 " 窗口传递的滚动字符串创建。  在计算表达式时，它会生成包含名称和变量类型或参数及其值的可打印的字符串。  此字符串在相应的 IDE 窗口中显示。  
  
## 实现  
 ，当程序在断点处停止后时，计算表达式。  该表达式由 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 接口表示，表示一个分析的表达式准备好在给定表达式计算上下文中的绑定和计算。  堆栈帧确定表达式计算上下文，调试引擎 \(DE\)提供通过实现 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口。  
  
 将用户字符串和 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口，调试引擎 \(DE\)可以通过将用户字符串获取 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 接口访问 [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法。  返回的 IDebugExpression2 接口包含已分析的表达式准备计算。  
  
 使用 [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)，使用 `IDebugExpression2` 接口， DE 通过同步或异步计算表达式可以获取该表达式的值，。  此值，与变量或参数。的名称和类型，发送到显示的 IDE。  该值、名称和类型由 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 接口表示。  
  
 若要启用表达式计算， DE 必须实现 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 和 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口。  同步和异步计算需要 [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法的实现。  
  
## 请参阅  
 [堆栈帧](../../extensibility/debugger/stack-frames.md)   
 [表达式计算上下文](../../extensibility/debugger/expression-evaluation-context.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)