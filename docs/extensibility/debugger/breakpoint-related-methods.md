---
title: "与断点相关的方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d743c98fd9e311f7f118c152e579178b07513d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoint-related-methods"></a>与断点相关的方法
调试引擎 (DE) 必须支持的设置的断点。 Visual Studio 调试支持以下类型的断点：  
  
-   绑定  
  
     通过 UI 请求并将其成功绑定到指定的代码位置  
  
-   挂起  
  
     通过 UI 但尚未绑定到实际说明请求  
  
## <a name="discussion"></a>讨论  
 例如，说明尚未加载时发生挂起断点。 当加载代码时，挂起断点 try，它是绑定到代码中的规定的位置，以的代码中插入中断说明。 事件发送到会话调试管理器 (SDM) 来指示成功的绑定或通知没有绑定错误。  
  
 挂起断点还管理自己的相应绑定断点的内部列表。 在代码中，一个挂起断点可能导致多个断点的插入。 Visual Studio 调试 UI 显示挂起断点的树视图和其对应的绑定断点。  
  
 创建和使用挂起断点需要实现[IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法，以及下列方法之一[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)接口。  
  
|方法|描述|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|确定指定挂起断点可以将绑定到的代码位置。|  
|[绑定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|将绑定指定挂起断点到一个或多个代码位置。|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|获取挂起断点的状态。|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|获取用于创建挂起断点的断点请求。|  
|[启用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切换挂起断点的启用的状态。|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|枚举绑定从挂起断点的所有断点。|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|枚举因挂起断点的所有错误断点。|  
|[删除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|删除挂起断点并从该绑定的所有断点。|  
  
 若要枚举的绑定的断点和错误断点，则必须实现的所有方法[IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)和[IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)。  
  
 挂起绑定到代码的断点位置需要实现以下[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)方法。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|获取包含断点的挂起断点。|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|获取绑定的断点的状态。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|获取描述断点的断点分辨率。|  
|[启用](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|启用或禁用断点。|  
|[删除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|删除绑定的断点。|  
  
 解决方法和请求信息需要实现以下[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)方法。  
  
|方法|描述|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|获取表示解析的断点的类型。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|获取描述断点的断点解析信息。|  
  
 绑定过程中可能发生的错误的解决方法需要实现以下[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)方法。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|获取包含错误断点挂起断点。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|获取描述错误断点的断点错误解析。|  
  
 绑定过程中可能发生的错误的解决方法还要求下列方法之一[IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)。  
  
|方法|描述|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|获取断点的类型。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|获取断点的解决方法信息。|  
  
 在断点处查看的源代码需要实现的方法[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)和/或方法的[IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。  
  
## <a name="see-also"></a>另请参阅  
 [执行控件和状态计算](../../extensibility/debugger/execution-control-and-state-evaluation.md)