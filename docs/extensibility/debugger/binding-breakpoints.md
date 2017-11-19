---
title: "绑定断点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 08000dddcd574d21225aa110cf9eb4ab2487aadb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="binding-breakpoints"></a>绑定断点
如果用户设置断点，可能通过按 F9，IDE 依照请求，将提示调试会话才能创建断点。  
  
## <a name="setting-a-breakpoint"></a>设置断点  
 设置断点是一个两步过程，，因为代码或由断点受影响的数据可能尚不可用。 首先，必须所述断点，然后，随着代码或数据变得可用，它必须绑定到该代码或数据，如下所示：  
  
1.  从相关的调试引擎 (DEs)、 请求断点，然后断点绑定到的代码或数据变得可用。  
  
2.  断点请求发送到调试会话中，将其发送到所有相关 DEs。 选择处理断点任何 DE 创建相应的挂起断点。  
  
3.  调试会话收集的挂起断点，并将其发送回调试包 （Visual Studio 的调试组件）。  
  
4.  调试包提示调试会话将挂起断点绑定到代码或数据。 调试会话将此请求发送到所有相关 DEs。  
  
5.  如果 DE 能够将断点绑定，它将发送回调试会话的断点绑定事件。 否则，它改为发送断点错误事件。  
  
## <a name="pending-breakpoints"></a>挂起断点  
 挂起断点可以绑定到多个代码位置。 例如，c + + 模板的源代码的行可以绑定到从模板生成每个代码序列。 调试会话可以使用断点绑定的事件以枚举在发送事件时绑定到断点的代码上下文。 可以从更高版本，绑定多个代码上下文，因此 DE 可能会发送多个断点绑定为每个绑定请求的事件。 但是，DE 应发送每个绑定请求只能有一个断点错误事件。  
  
## <a name="implementation"></a>实现  
 以编程方式，调试包调用会话调试管理器 (SDM)，并为其提供[IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)包装的接口[BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md)结构，其中介绍了要设置的断点。 尽管断点可以为多种形式，但它们是最终解析为代码或数据上下文的过程。  
  
 SDM 通过调用传递到每个相关 DE 此调用其[CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法。 如果 DE 选择处理断点，它将创建并返回[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)接口。 SDM 收集这些接口，并将它们传递给调试包作为单个返回`IDebugPendingBreakpoint2`接口。  
  
 到目前为止，已不生成任何事件。  
  
 调试包然后尝试将挂起断点绑定到代码或数据，通过调用[绑定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)，由 DE 实现。  
  
 如果绑定断点，DE 发送[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)到调试包的事件接口。 此接口可枚举所有代码上下文 （或单个数据上下文） 通过调用绑定到断点调试包使用[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)，这将返回一个或多个[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)接口。 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)接口返回[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)接口，和[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)返回[BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)联合包含的代码或数据上下文。  
  
 如果 DE 不能将断点绑定，则将发送单个[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)到调试包的事件接口。 调试包检索的错误类型 （错误或警告） 和信息性消息，通过调用[GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)后, 跟[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)和[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)。 这将返回[BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md)包含错误类型和消息的结构。  
  
 如果 DE 处理断点，但不能将其绑定，它将返回类型的错误`BPET_TYPE_ERROR`。 调试包就会显示错误对话框，并 IDE 放置在源代码行左侧的断点标志符号感叹号标志符号。  
  
 如果 DE 处理断点，无法绑定，但某些其他 DE 可能将其绑定，则会返回警告。 通过将放置在断点标志符号的源代码行左侧的问题标志符号时，IDE 做出响应。  
  
## <a name="see-also"></a>另请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)