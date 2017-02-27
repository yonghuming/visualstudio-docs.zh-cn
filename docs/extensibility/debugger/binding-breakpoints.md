---
title: "绑定断点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "绑定的断点"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 绑定断点
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

如果用户设置断点，可能按 F9， IDE 地方请求并提示调试会话创建断点。  
  
## 设置断点  
 ，因为断点的数据或影响的代码可能不可用，设置断点过程分为两步。  首先，必须描述断点，然后，代码时，或数据可用，则必须绑定到该代码或数据，如下所示:  
  
1.  断点相关请求调试引擎 \(DEs\)，断点然后绑定到代码或数据，则将变得可用。  
  
2.  断点请求发送到调试会话，将其发送到所有相关 DES。  选择处理断点的所有 DE 创建相应等待断点。  
  
3.  调试会话集合挂起的断点并将其添加到调试包 \(Visual Studio 调试组件\)。  
  
4.  调试包提示调试会话挂起的绑定断点代码或数据。  调试会话发送此请求到所有相关 DES。  
  
5.  如果 DE 可以将断点时，它将断点绑定事件为调试会话。  否则，它发送断点错误事件。  
  
## 等待断点  
 挂起断点可以绑定到多个代码位置。  例如，源代码行 c. c\+\+ 模板的可绑定到从模板生成的每个代码序列。  ，在发送后，调试会话可以使用断点绑定事件枚举代码上下文绑定到断点事件。  更多代码上下文可在以后必须，因此， DE 可以发送多个断点每个绑定请求的绑定事件。  但是， DE 只应该将每个绑定请求一个断点错误事件。  
  
## 实现  
 编程方式，调试包召开会议调试管理器 \(SDM\)并将该包装一 [BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md) 结构，描述要设置断点的 [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 接口。  虽然断点可以为多种形式，它们最终解析为代码或数据上下文。  
  
 SDM 通过此调用每个相关 DE 通过调用其 [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 方法。  如果 DE 选择处理断点，它会创建并返回一 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 接口。  SDM 收集这些接口并将其回调试打包成单个 `IDebugPendingBreakpoint2` 接口。  
  
 到目前为止，事件未生成。  
  
 调试包然后尝试将挂起的断点通过调用 [将绑定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)代码或数据，由 DE 实现。  
  
 如果断点绑定， DE 发送一 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 事件接口到调试包。  调试包使用此接口枚举所有代码上下文 \(或单个数据上下文\) 限制对断点通过调用 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)，返回一个或多 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 接口。  [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) 接口返回 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 接口，并且， [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 返回包含代码或数据上下文的 [BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) 联合。  
  
 如果 DE 无法将断点，它发送一个 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 事件接口到调试包。  调试包通过调用 [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)检索错误类型 \(错误或警告\) 和信息性消息，后跟 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 和 [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)。  这将返回包含错误类型和消息的 [BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) 结构。  
  
 如果 DE handles 断点，但不能将其绑定，它返回类型 `BPET_TYPE_ERROR`错误。  调试包通过显示错误对话框响应，并且， IDE 在源代码行左侧放置在断点标志符号中的感叹号标志符号。  
  
 如果 DE handles 断点，不能将其绑定，但是，某些其他 DE 可能将其绑定，它将返回警告。  IDE 通过将在断点标志符号中的问题标志符号响应在源代码行左侧。  
  
## 请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)