---
title: "IDebugBreakpointRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2 接口"
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示必需的信息创建和绑定任何类型的断点。  
  
## 语法  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## 实现者说明  
 会议调试管理器 \(SDM\)通常实现此接口。  
  
## 调用方的说明  
 调试引擎 \(DE\)通过调用接收此接口来 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 以创建挂起的断点。  为 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) 的调用可以从、检索此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugBreakpointRequest2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|获取该断点请求的断点位置类型。|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|获取描述该断点请求的断点请求信息。|  
  
## 备注  
 正在调试的程序后处理在程序中加载了，对 [将绑定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 绑定的调用请求的位置挂起的断点。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [将绑定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)