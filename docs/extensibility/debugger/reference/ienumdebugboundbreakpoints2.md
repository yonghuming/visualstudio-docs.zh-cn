---
title: "IEnumDebugBoundBreakpoints2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2"
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举绑定断点与挂起的断点或断点绑定事件。  
  
## 语法  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口作为其一部分为断点支持。  此接口，如果断点支持，必须实现。  
  
## 调用方的说明  
 Visual Studio 会调用:  
  
-   获取此接口的[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 表示触发所有断点的列表。  
  
-   获取此接口的[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 表示给所有断点的列表。  
  
-   获取此接口的[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) 表示任何断点列表绑定到该挂起的断点。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugBoundBreakpoints2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|检索绑定断点指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|跳过绑定断点指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|获取绑定断点数在枚举数。|  
  
## 备注  
 Visual Studio 使用此接口表示的绑定断点更新断点在 IDE 中显示。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)