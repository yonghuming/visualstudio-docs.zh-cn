---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定是否应异常传递给正在调试的程序，当执行恢复，或者，如果应丢弃异常。  
  
## 语法  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### 参数  
 `fPass`  
 \[in\] 非零 \(`TRUE`\)，如果异常应传递到正在调试的程序，当执行恢复，或者零 \(0\)`FALSE`\)，则应丢弃异常。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 调用此方法在正在调试的程序实际上不会导致任何代码执行。  调用仅仅是设置代码执行的状态。  例如，对 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 方法可返回 `S_OK` 和 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)。`dwState` 字段设置为 `EXCEPTION_STOP_SECOND_CHANCE`。  
  
 IDE 会接收 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 事件和调用 [继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md) 方法。  调试引擎 \(DE\)应具有默认行为处理用例 `PassToDebuggee` 方法没有被调用。  
  
## 请参阅  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md)