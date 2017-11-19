---
title: "IDebugEventCallback2::Event |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2::Event
helpviewer_keywords: IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c1a69c3ce3a8b59c1cea7b9282d0169c3637729
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
发送的调试事件的通知。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pEngine`  
 [in][IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)表示发送此事件的调试引擎 (DE) 的对象。 DE 需要填写此参数。  
  
 `pProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)表示发生事件的过程的对象。 由会话调试管理器 (SDM) 填充此参数。 DE 始终传递此参数的 null 值。  
  
 `pProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)表示的程序发生此事件的对象。 对于大多数事件，此参数不是 null 值。  
  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)表示发生此事件的线程的对象。 用于停止事件，此参数不能为 null 值，从此参数获取堆栈帧。  
  
 `pEvent`  
 [in][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)表示调试事件的对象。  
  
 `riidEvent`  
 [in]GUID，标识哪些事件接口以从获取`pEvent`参数。  
  
 `dwAttrib`  
 [in]中的标志的组合[EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)枚举。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 调用此方法时`dwAttrib`参数必须与从返回的值匹配[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)方法，如在事件对象上调用传入`pEvent`参数。  
  
 无论是否事件本身是异步的或不以异步方式发布所有调试事件。 当 DE 调用此方法时，返回的值不指示是否处理事件，仅是否收到事件。 事实上，在大多数情况下，事件尚未处理此方法返回时。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)