---
title: "IDebugExpression2::EvaluateAsync | Microsoft Docs"
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
  - "IDebugExpression2::EvaluateAsync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateAsync"
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法计算表达式异步。  
  
## 语法  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```c#  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### 参数  
 `dwFlags`  
 \[in\] 标志的组合。 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 枚举的该控件表达式计算。  
  
 `pExprCallback`  
 \[in\] 此参数始终是 null 值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  典型的错误代码为:  
  
|错误|说明|  
|--------|--------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|另一个表达式当前，都计算，并同时表达式计算不受支持。|  
  
## 备注  
 ，了在启动表达式计算之后，此方法应返回。  在表达式成功计算时，必须发送 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 到 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 事件回调由提供通过 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) 或 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
## 示例  
 下面的示例演示如何执行简单的 `CExpression` 对象的方法实现 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 接口。  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## 请参阅  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)