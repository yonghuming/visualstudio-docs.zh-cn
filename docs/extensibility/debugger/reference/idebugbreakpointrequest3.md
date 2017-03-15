---
title: "IDebugBreakpointRequest3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3"
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示必需的信息创建和绑定任何类型的断点。  它是 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)扩展。  
  
## 语法  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## 实现者说明  
 会议调试管理器 \(SDM\)通常实现此接口。  
  
## 调用方的说明  
 此接口通过调用 IDebugBreakpointRequest2 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 在调用收到对 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)的调试引擎 \(DE\)访问。  
  
## 方法按 Vtable 顺序  
 除了从 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 继承的方法之外，`IDebugBreakpointRequest3` 接口还公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|获取描述该断点请求的断点请求信息。|  
  
## 备注  
 此接口用于提供附加信息。 DE 通过 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 结构。  此附加信息包括 DE 的供应商 ID \(使用 GUID 的形式\)，跟踪点的名称和断点约束的名称。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)