---
title: "IDebugThread2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 363f2aa684d45a07978c70b222af7f35ea2b05d3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2"></a>IDebugThread2
此接口表示在程序中运行的线程。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口来表示的单个程序中的执行线程。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)来获取表示当前处于活动状态的线程此接口。  
  
 此接口还用于创建断点请求 (请参阅[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md))。  
  
 在解析绑定或错误断点时，也会返回此接口 (请参阅[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)和[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md))。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugThread2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|检索此线程的堆栈帧的列表。|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|获取线程的名称。|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|设置线程的名称。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|获取线程正在运行的程序。|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|确定是否可以为给定的堆栈帧和代码上下文设置下一条语句。|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|将下一条语句设置为给定的堆栈帧和代码上下文。|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|获取系统线程标识符。|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|挂起线程。|  
|[恢复](../../../extensibility/debugger/reference/idebugthread2-resume.md)|继续的线程。|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|获取用于描述一个线程的属性。|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|获取与此物理线程关联的逻辑线程。|  
  
## <a name="remarks"></a>备注  
 因为一个物理线程可以运行在多个程序中，多个`IDebugThread2`从多个程序可以表示同一个物理线程。  
  
 断点或异常发生时，发送事件，通过调用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。 此方法的参数之一是`IDebugThread2`表示当前线程的接口。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)用于获取[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)当前堆栈帧的接口。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
