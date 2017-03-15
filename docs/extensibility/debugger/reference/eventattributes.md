---
title: "EVENTATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "EVENTATTRIBUTES 枚举"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定事件属性。  
  
## 语法  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## 成员  
 EVENT\_ASYNCHRONOUS  
 指示该操作是异步的和向事件的否定答案是必需的。  
  
 EVENT\_SYNCHRONOUS  
 指示该操作是同步;通过 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)的答案。  
  
 EVENT\_STOPPING  
 指示这是一个停止点的事件。  必须将与 `EVENT_ASYNCHRONOUS` 或 `EVENT_SYNCHRONOUS`。  
  
 EVENT\_ASYNC\_STOP  
 指示异步终止的事件。  当前没有这样的事件。  此标志仅占位符。  
  
 EVENT\_SYNC\_STOP  
 指示一个同步终止的事件 \( `EVENT_SYNCHRONOUS` 和 `EVENT_STOPPING`的组合\)。  ，当它发送一个停止点的事件时，调试引擎 \(DE\)使用此值。  答案通过调用可对 [执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)、 [单步执行](../../../extensibility/debugger/reference/idebugprogram2-step.md)或 [继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。  
  
 EVENT\_IMMEDIATE  
 指示立即和同步发送到 IDE 的事件。  此标志组合与 `EVENT_ASYNCHRONOUS`、 `EVENT_SYNCHRONOUS`或 `EVENT_SYNC_STOP` 的其他标志指示操作和该条件的类型答案结构 \(如果有\) 了解。  
  
 EVENT\_EXPRESSION\_EVALUATION  
 事件是表达式计算的结果。  
  
## 备注  
 这些值在 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 方法的 `dwAttrib` 参数传递。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)