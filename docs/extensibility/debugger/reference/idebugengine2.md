---
title: "IDebugEngine2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2
helpviewer_keywords: IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f684a29eea526f7725e8a876f53453512f65dadc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2"></a>IDebugEngine2
此接口表示调试引擎 (DE)。 它用于从创建到设置和清除异常的断点管理调试会话的各个方面。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 自定义 DE 管理调试的程序通过实现此接口。 必须通过 DE 实现此接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口称为会话调试管理器 (SDM) 来管理调试会话，包括管理异常、 创建断点，以及对同步 DE 所发送的事件作出响应。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugEngine2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|创建由 DE 正在调试的所有程序的一个枚举器。|  
|[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)|将 DE 附加到程序。|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|创建在 DE 挂起断点。|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|指定 DE 应如何处理给定的异常。|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|删除指定的异常，以便不再由的调试引擎。|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|删除 IDE 已为特定的运行时体系结构或语言设置的异常的列表。|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|获取 DE 的 GUID。|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|通知已异常终止指定的程序和 DE 应清除对该程序的所有引用并发送程序 DE 销毁事件。|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|由 SDM 以指示同步调试事件，以前发送到 SDM，DE 已接收和处理调用。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|设置 DE 的区域设置。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|由 DE 使用当前设置的注册表根。|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|设置某个度量值。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|通过此 DE 正在调试的所有程序都停止执行其线程之一尝试运行下一次的请求。|  
  
## <a name="requirements"></a>要求  
 标头： Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)