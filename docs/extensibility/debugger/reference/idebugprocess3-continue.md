---
title: "IDebugProcess3::Continue | Microsoft Docs"
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
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

继续运行此从一种状态中止处理。  所有以前执行状态 \(例如步骤\) 保留和处理再次开始执行。  
  
> [!NOTE]
>  应使用此方法而不是 [继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。  
  
## 语法  
  
```cpp  
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
 \[in\] 表示线程的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象将继续。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法调用此过程无论多少进程进行调试，或者的过程生成已停止的事件。  实现必须保留以前执行状态 \(例如步骤\) 和继续执行，就象在完成其前面执行之前从未停止。  也就是说，如果线程中执行过程中的步骤操作并已停止运行，因为某些其他进程停止， `Continue` 然后调用，指定的线程必须完成步骤操作的初始。  
  
 **警告**不发送一个终止的事件或一个即时 \(\) 同步事件。 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ，当处理此时调用，否则调试器会停止。  
  
## 请参阅  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)