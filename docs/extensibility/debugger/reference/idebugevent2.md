---
title: "IDebugEvent2 | Microsoft Docs"
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
  - "IDebugEvent2"
helpviewer_keywords: 
  - "IDebugEvent2 接口"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口用于传达重要调试信息，例如停止在断点并不重要的信息，例如调试消息。  
  
## 语法  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)和自定义端口提供程序实现在对象的此接口和其他事件接口相同。  
  
## 调用方的说明  
 使用接口 ID \(IID\) 参数为 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 或 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)，会议调试管理器 \(SDM\)对 `IDebugEvent2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取相应的事件接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|获取此的属性调试事件。|  
  
## 备注  
 更具体的事件接口，如 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)，从 IDebugEvent2 接口派生，但是实现为对象的单独的接口和 `IDebugEvent2`相同。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)