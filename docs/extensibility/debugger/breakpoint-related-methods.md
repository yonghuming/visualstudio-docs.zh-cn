---
title: "断点相关的方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，断点方法"
  - "断点、 方法"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 断点相关的方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)必须支持设置断点。  Visual Studio 调试支持断点的以下类型:  
  
-   绑定  
  
     请求通过 UI 并成功绑定到指定的代码位置  
  
-   挂起  
  
     请求通过 UI，但不绑定到实际命令  
  
## 讨论  
 例如，在中，如果命令未加载时，挂起的断点发生。  在加载代码时，等待断点请尝试将建议代码的位置，即，插入到代码中中断命令。  事件发送给会话调试管理器 \(SDM\)指示成功的绑定或通知具有约束错误。  
  
 挂起断点还管理自己内部列表对应的绑定断点。  一个等待断点在代码可能导致许多断点插入。  调试 UI 的 Visual Studio 显示挂起的断点及其相应的绑定断点树视图。  
  
 为 " 挂起 " 断点的创建和使用需要 [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 方案和 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 接口下列方法的实现。  
  
|方法|说明|  
|--------|--------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|确定指定等待断点是否可以绑定到代码位置。|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|绑定指定等待导出到一个或多个代码位置。|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|获取挂起的断点的状态。|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|获取断点请求用于创建挂起的断点。|  
|[启用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切换挂起的断点的启用状态。|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|枚举从 " 挂起的断点绑定的所有断点。|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|枚举由挂起的断点的所有错误断点。|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|从中删除必须挂起的断点和所有断点。|  
  
 若要枚举绑定断点和错误断点，必须执行 [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 所有方法和 [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)。  
  
 等待绑定到代码位置的断点需要以下 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 方法的实现。  
  
|方法|说明|  
|--------|--------|  
|[GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)|获取包含断点的挂起的断点。|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|获取绑定断点的状态。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|获取描述断点的断点解析。|  
|[启用](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|启用或禁用断点。|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|删除绑定断点。|  
  
 分辨率和请求信息需要以下 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 方法的实现。  
  
|方法|说明|  
|--------|--------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|获取解析表示断点的类型。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|获取描述断点的断点解析信息。|  
  
 可能会在绑定期间错误的解决方法需要以下 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 方法的实现。  
  
|方法|说明|  
|--------|--------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|获取包含错误断点的挂起的断点。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|获取描述错误断点的断点错误解析。|  
  
 可能发生在同时绑定期间错误的解决方法要求 [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)以下方法。  
  
|方法|说明|  
|--------|--------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|获取断点的类型。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|获取断点的分辨率信息。|  
  
 查看断点的源代码需要执行 [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 方法和\/或 [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)方法。  
  
## 请参阅  
 [执行控制和状态评估](../../extensibility/debugger/execution-control-and-state-evaluation.md)