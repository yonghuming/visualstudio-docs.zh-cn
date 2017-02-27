---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2 接口"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示准备绑定到代码位置的断点。  
  
## 语法  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口作为其一部分为断点支持。  
  
## 调用方的说明  
 为 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 的调用创建从 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 接口的挂起的断点。  为 [将绑定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 的调用创建表示在程序中有限的一个断点 `IDebugBreakpoint2` 接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPendingBreakpoint2`方法。  
  
|方法|说明|  
|--------|--------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|确定此挂起的断点是否可以绑定到代码位置。|  
|[将绑定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|将此挂起的断点到一个或多个代码位置。|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|获取挂起的断点状态。|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|获取用于创建此挂起的断点的断点请求。|  
|[虚拟化](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|切换此挂起的断点有效状态。|  
|[启用](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切换此挂起的断点已启用状态。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|设置或更改该条件与此挂起的断点。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|设置或更改通过计数与此挂起的断点。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|枚举从此挂起的断点绑定的所有断点。|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|枚举由此挂起的断点的所有错误断点。|  
|[删除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|从中删除绑定的此挂起的断点和所有断点。|  
  
## 备注  
 `IDebugPendingBreakpoint2` 可视为必要所需的所有信息提供程序绑定可应用于一个或多个程序的断点代码。  
  
 挂起断点可能导致多个绑定断点。  例如，在 c. c\+\+ 样式模板的断点会导致该模板的每个实例都绑定断点。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)