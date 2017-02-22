---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
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
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在特定允许线程 \(或禁止\) 表达式计算结果，因此，即使程序停止。  
  
## 语法  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### 参数  
 `pOriginatingProgram`  
 \[in\] 表示计算表达式的程序的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象。  
  
 `dwTid`  
 \[in\] 指定线程的标识符。  
  
 `dwEvalFlags`  
 \[in\] 指定标志的组合。 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 枚举的计算方式执行。  
  
 `pExprCallback`  
 \[in\] 要使用的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 对象发送调试在计算表达式时发生的事件。  
  
 `fWatch`  
 \[in\] 如果非零 \(`TRUE`\)，允许在 `dwTid`确定线程的表达式计算;否则，零 \(0\)`FALSE`\) 禁止该线程的表达式计算。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 在会议调试时管理器 \(SDM\)要求程序，这是由 `pOriginatingProgram` 参数，计算表达式，它通过调用此方法以通知其他附加程序。  
  
 在一个程序的表达式计算在另一个可导致代码运行，因为函数的所有 `IDispatch` 属性的计算或计算。  因此，此方法允许表达式计算运行和完成，即使线程在此程序可以停止。  
  
## 请参阅  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)