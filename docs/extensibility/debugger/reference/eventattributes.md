---
title: "EVENTATTRIBUTES |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVENTATTRIBUTES
helpviewer_keywords: EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097a61ff6c96fd4901265ad960169fd5ec7244c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
指定的事件属性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>成员  
 EVENT_ASYNCHRONOUS  
 指示事件是异步的需要事件没有收到回复。  
  
 EVENT_SYNCHRONOUS  
 指示事件是同步的通过答复[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)。  
  
 EVENT_STOPPING  
 指示这是一个停止事件。 必须结合使用`EVENT_ASYNCHRONOUS`或`EVENT_SYNCHRONOUS`。  
  
 EVENT_ASYNC_STOP  
 表示一个异步停止事件。 当前没有此类事件。 此标志只是一个占位符。  
  
 EVENT_SYNC_STOP  
 指示同步停止事件 (的组合`EVENT_SYNCHRONOUS`和`EVENT_STOPPING`)。 在发送 stopping 事件时，将由调试引擎 (DE) 使用此值。 通过调用进行答复[执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)，[步骤](../../../extensibility/debugger/reference/idebugprogram2-step.md)，或[继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。  
  
 EVENT_IMMEDIATE  
 表示一个事件到 IDE 发送立即和同步。 此标志结合了多个等其他标志`EVENT_ASYNCHRONOUS`， `EVENT_SYNCHRONOUS`，或`EVENT_SYNC_STOP`以指示的事件，并在答复机制 （如果有） 已知类型。  
  
 EVENT_EXPRESSION_EVALUATION  
 事件是计算的表达式结果。  
  
## <a name="remarks"></a>备注  
 这些值会传递中`dwAttrib`参数[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。  
  
 这些值可以与按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)