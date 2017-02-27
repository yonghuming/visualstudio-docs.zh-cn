---
title: "IDebugProcess3::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

生成处理到第一步命令或语句。  
  
> [!NOTE]
>  应使用此方法而不是 [单步执行](../../../extensibility/debugger/reference/idebugprogram2-step.md)。  
  
## 语法  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### 参数  
 `pThread`  
 \[in\] 表示线程的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象步骤。  
  
 `sk`  
 \[in\] 一个 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 值。  
  
 `step`  
 \[in\] 一个 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 值。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则返回错误代码。  
  
## 备注  
 如果有任何线程同步或通信线程之间，其他线程在进程应运行，在特定线程上执行时。  
  
 **警告**不发送一个终止的事件或一个即时 \(\) 同步事件。 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ，当处理此时调用，否则调试器会停止。  
  
## 请参阅  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)