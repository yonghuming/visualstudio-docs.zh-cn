---
title: "IDebugExpression2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpression2
helpviewer_keywords: IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ba89642b51d4b1d471bc6c46d84441c6383005c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpression2"></a>IDebugExpression2
此接口表示准备绑定和评估之间的已分析的表达式。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口来表示准备要进行求值的已分析的表达式。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)返回此接口。 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)返回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口。 仅当已暂停正在调试的程序，堆栈帧可用时，这些接口是可访问。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugExpression2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以异步方式计算此表达式。|  
|[中止](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|结束异步表达式计算。|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式计算此表达式。|  
  
## <a name="remarks"></a>备注  
 当程序已暂停时，会话调试管理器 (SDM) 堆栈帧将从获取通过调用 DE [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 然后调用 SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)获取[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口。 这一切后跟调用[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)创建`IDebugExpression2`接口，表示已分析的准备要进行求值表达式。  
  
 SDM 调用[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)实际评估表达式并生成一个值。  
  
 中的实现`IDebugExpressionContext2::ParseText`，DE 使用 COM 的`CoCreateInstance`函数来实例化的表达式计算器和获取[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)接口 (请参阅中的示例`IDebugExpressionEvaluator`接口)。 然后调用 DE[分析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)获取[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)接口。 实现中使用此接口`IDebugExpression2::EvaluateSync`和`IDebugExpression2::EvaluateAsync`要执行计算。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)