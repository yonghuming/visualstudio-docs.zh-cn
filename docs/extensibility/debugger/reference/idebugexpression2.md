---
title: "IDebugExpression2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2"
helpviewer_keywords: 
  - "IDebugExpression2 接口"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示一个分析的表达式准备绑定和计算。  
  
## 语法  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示准备一个分析的计算表达式。  
  
## 调用方的说明  
 为 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 的调用返回此接口。  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 返回 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口。  这些接口可访问，仅当正在调试的程序暂停，而堆栈帧可用。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugExpression2`方法。  
  
|方法|说明|  
|--------|--------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|此表达式计算异步。|  
|[中止](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|结束异步计算表达式。|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|同步此表达式计算。|  
  
## 备注  
 当程序暂停后，该会话调试管理器 \(SDM\)从 DE 的一个堆栈帧的调用。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。  SDM 然后调用 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 获取 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口。  这通过对 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 的调用执行创建 `IDebugExpression2` 接口，表示准备已分析的计算表达式。  
  
 SDM 调用 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 实际计算表达式和生成值。  
  
 在 `IDebugExpressionContext2::ParseText`的实现，实例化表达式计算器和捕获 DE 使用 COM 的 `CoCreateInstance` 功能 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 接口 \(参见中 `IDebugExpressionEvaluator` 接口的示例\)。  DE 然后调用 [分析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 获取 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 接口。  此接口用于 `IDebugExpression2::EvaluateSync` 和 `IDebugExpression2::EvaluateAsync` 的实现执行计算。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)