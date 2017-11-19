---
title: "IDebugEventCallback2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2
helpviewer_keywords: IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1218be6316740b50ebd7446848ee1bd3352b122e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
调试引擎 (DE) 使用此接口来将调试事件发送到会话调试管理器 (SDM)。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]实现此接口可从调试引擎接收事件。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调试引擎通常接收此接口，当 SDM 调用[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)，[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)，或[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。 调试引擎通过调用将事件发送至 SDM[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugEventCallback2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|发送通知的调试事件，以便将 SDM。|  
  
## <a name="remarks"></a>备注  
 尽管[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)和[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)指定它们需要`IDebugEventCallback2`接口，这不是这样，和的接口指针将始终为 null 值。 相反，必须使用的调试引擎`IDebugEventCallback2`接口的调用中接收[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)，[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)，或[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
 如果包实现[IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md)在托管代码中，强烈建议，<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>传递给在各种接口上调用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)