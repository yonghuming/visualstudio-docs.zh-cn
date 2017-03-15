---
title: "IDebugEventCallback2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

发送通知调试事件。  
  
## 语法  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```c#  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### 参数  
 `pEngine`  
 \[in\] 表示调试引擎 \(DE\)发送此事件的 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 对象。  要求、填写此参数。  
  
 `pProcess`  
 \[in\] 表示处理该事件的发生 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 对象。  此参数由会议填充调试管理器 \(SDM\)。  DE 始终将此参数的 null 值。  
  
 `pProgram`  
 \[in\] 表示程序发生此事件的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象。  对于大多数操作，此参数不是 null 值。  
  
 `pThread`  
 \[in\] 表示线程时发生此事件的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。  若要停止，当堆栈帧从此参数，获取事件，此参数不能是 null 值。  
  
 `pEvent`  
 \[in\] 表示调试事件的 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 对象。  
  
 `riidEvent`  
 \[in\] 标识获取的事件接口从 `pEvent` 参数的 GUID。  
  
 `dwAttrib`  
 \[in\] 标志的组合。 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 枚举的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 当调用此方法， `dwAttrib` 参数必须匹配时从 [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) 方法返回的值作为调用了 `pEvent` 参数传递的事件对象。  
  
 所有调试事件发送异步，无论操作是异步的。  当 DE 调用此方法时，返回值指示无事件是否处理，该操作只有是否接收。  实际上，在中，当此方法返回时，在大多数情况下，事件未处理。  
  
## 请参阅  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)