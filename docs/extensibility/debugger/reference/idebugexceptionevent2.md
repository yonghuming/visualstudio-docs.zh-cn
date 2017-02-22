---
title: "IDebugExceptionEvent2 | Microsoft Docs"
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
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "IDebugExceptionEvent2 接口"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

，当异常在当前执行的程序时，会引发调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)。  
  
## 语法  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 报告此接口的异常正在调试的程序发生。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  
  
## 调用方的说明  
 DE 创建和发送此事件对象报告异常。  事件发送使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试的程序。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugExceptionEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetException](../Topic/IDebugExceptionEvent2::GetException.md)|有关激发此事件的异常的 Gets 详细信息。|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|获取激发此事件时引发的异常的一个可读的说明。|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|确定是否 \(DE\)调试引擎通过此异常的选项传递给正在调试的程序，当执行恢复。|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|指定是否应异常传递给正在调试的程序，当执行恢复，或者，如果应丢弃异常。|  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 备注  
 在发送事件之前， DE 检查此异常事件是否已指定了首次或由前面的第二次异常调用 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)。  如果它被指定为首次异常， `IDebugExceptionEvent2` 事件发送到 SDM。  否则， DE 为应用程序有机会处理异常。  如果未提供异常处理程序，，并且，如果异常被指定为是第二次异常， `IDebugExceptionEvent2` 事件发送到 SDM。  否则， DE 继续执行程序时和操作系统或运行时异常。  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)