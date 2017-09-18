---
title: "IDebugProgram2::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

执行一步。  
  
> [!NOTE]
>  此方法已被否决。  请改用 [单步执行](../../../extensibility/debugger/reference/idebugprocess3-step.md) 方法。  
  
## 语法  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### 参数  
 `pThread`  
 \[in\] 表示单步执行的线程的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。  
  
 `sk`  
 \[in\] 从指定步骤的 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 枚举的值。  
  
 `step`  
 \[in\] 从如指定步骤单元测试的 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 枚举的值 \(，由语句或命令\)。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 如果有任何线程同步或通信线程之间，其他线程在程序应运行，在特定线程上执行时。  
  
> [!WARNING]
>  不要将一个终止的事件或一个即时 \(\) 同步事件。 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ，当处理此时调用，否则调试器会停止。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)