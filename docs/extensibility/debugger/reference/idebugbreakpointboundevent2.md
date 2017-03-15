---
title: "IDebugBreakpointBoundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointBoundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointBoundEvent2"
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointBoundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口一个会话调试管理器 \(SDM\)挂起的断点成功绑定到一个加载程序。  
  
## 语法  
  
```  
IDebugBreakpointBoundEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE 作为它的部分此接口为断点支持的 implements。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同 \(SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口\)。  
  
## 调用方的说明  
 ，当挂起的断点成功绑定到已调试时，的程序、创建和发送此事件对象。  ，它附加到正在调试的程序，该事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugBreakpointBoundEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|获取必须挂起的断点。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|创建此事件绑定断点的枚举器。|  
  
## 备注  
 每当断点绑定，事件发送到 SDM。  如果断点不能绑定，发送 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) ;否则，发送 `IDebugBreakpointBoundEvent2` 。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)