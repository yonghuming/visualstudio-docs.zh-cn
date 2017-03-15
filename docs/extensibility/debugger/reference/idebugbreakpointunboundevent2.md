---
title: "IDebugBreakpointUnboundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointUnboundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2"
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口一个会话调试管理器 \(SDM\)绑定断点从一个加载程序断开连接。  
  
## 语法  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口作为其一部分为断点支持。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同 \(SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口\)。  
  
## 调用方的说明  
 ，当绑定断点中断时，、创建和发送此事件对象。  ，它附加到正在调试的程序，该事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugBreakpointUnboundEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|获取变为未绑定断点。|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|获取断点是未绑定的原因。|  
  
## 备注  
 在调试引擎 DLL 或类卸载时，绑定到该模块中的代码的所有断点必须是未绑定从正在调试的程序。  `IDebugBreakpointUnboundEvent2` 为每个未绑定断点发送。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)