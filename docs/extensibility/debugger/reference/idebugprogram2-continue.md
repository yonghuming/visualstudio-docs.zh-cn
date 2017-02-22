---
title: "IDebugProgram2::Continue | Microsoft Docs"
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
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

继续运行从一种停止状态的此过程。  所有以前执行状态 \(例如步骤\) 保留和程序再次开始执行。  
  
> [!NOTE]
>  此方法已被否决。  请改用 [继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 方法。  
  
## 语法  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### 参数  
 `pThread`  
 \[in\] 表示线程的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法调用此过程无论多少程序进行调试，或者要程序生成已停止的事件。  实现必须保留以前执行状态 \(例如步骤\) 和继续执行，就象在完成其前面执行之前从未停止。  也就是说，如果在此过程中的线程执行中的步骤操作并已停止运行，因为某些其他程序终止的，则此方法调用，程序必须完成步骤操作的初始。  
  
> [!WARNING]
>  不要将一个终止的事件或一个即时 \(\) 同步事件。 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ，当处理此时调用，否则调试器会停止。  
  
## 请参阅  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)