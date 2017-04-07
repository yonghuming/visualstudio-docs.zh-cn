---
title: "IDebugCanStopEvent2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 00cfe8409762119c15cbe188b1a20b7a6466ea4a
ms.lasthandoff: 04/05/2017

---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
使用此接口来询问会话调试管理器 (SDM) 是否停止在当前的代码位置。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口以支持单步执行源代码。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)接口必须实现该接口对同一个对象 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)访问`IDebugEvent2`接口)。  
  
 此接口的实现必须通信的 SDM 调用[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)到的调试引擎。 例如，这可通过消息发布到的调试引擎的消息处理线程或实现此接口的对象无法保存对的调试引擎的引用和回调到的调试引擎使用标志传递给`IDebugCanStopEvent2::CanStop`。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 DE 可以发送此方法要求 DE 继续执行，DE 每次逐句通过代码。 通过使用发送此事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM 时将其附加到正在调试的程序所提供的回调函数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugCanStopEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|获取此事件的原因。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|指定被调试的程序是否应在此事件 （和发送描述停止的原因的事件） 的位置停止或只需继续执行。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|获取描述此事件的位置的文档上下文。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|获取描述此事件的位置的代码上下文。|  
  
## <a name="remarks"></a>备注  
 如果此用户单步执行函数，DE 查找任何调试信息或调试信息存在但 DE 不知道如果可以为该位置显示的源代码，DE 将发送此接口。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
