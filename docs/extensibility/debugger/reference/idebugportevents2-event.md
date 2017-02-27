---
title: "IDebugPortEvents2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2::Event"
helpviewer_keywords: 
  - "IDebugPortEvents2::Event"
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法会表示，以创建和销毁处理和位于端口的程序的事件。  
  
## 语法  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```c#  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### 参数  
 `pMachine`  
 \[in\] 表示调试服务器的 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 对象 \(有一个 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]每个实例的\) 会发生事件。  
  
 `pPort`  
 \[in\] 表示端口发生此事件的 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 对象。  
  
 `pProcess`  
 \[in\] 表示处理该事件的发生 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 对象。  
  
 `pProgram`  
 \[in\] 表示程序发生此事件的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象。  
  
 `pEvent`  
 \[in\] 标识事件的 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 对象。  可能的事件如下所示:  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 \[in\] 事件的 GUID。  由于事件转换到调用此方法之前的 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) ，此标识符可以更轻松地确定发送哪个事件。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)