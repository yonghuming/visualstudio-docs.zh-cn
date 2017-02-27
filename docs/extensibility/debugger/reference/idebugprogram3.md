---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3 接口"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示进程中运行的程序并通过提供线程信息扩展 [执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md) 。  
  
## 语法  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## 实现者说明  
 调试引擎 \(DE\)和自定义端口提供程序实现此接口表示进程中的程序。  会议调试管理器 \(SDM\)还实现此接口提供信息 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。  
  
## 调用方的说明  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件返回一个新过程的此接口。  此接口还用作参数为多个接口中的许多方法。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProgram3`方法。  
  
|方法|说明|  
|--------|--------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|执行程序。  线程返回提供线程用户看到，在执行的调试器信息。|  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 备注  
 ，而过程由一个或多个程序组成，程序是运行在特定运行时结构中的线程容器。  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [下一步](../Topic/IEnumDebugPrograms2::Next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)