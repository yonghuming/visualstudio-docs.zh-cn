---
title: "IDebugMessageEvent2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
此接口通过调试引擎 (DE) 用于将消息发送到需要一个响应来自用户的 Visual Studio。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 DE 实现此接口以将消息发送到需要用户响应的 Visual Studio。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)接口必须实现该接口对同一个对象。 使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)访问`IDebugEvent2`接口。  
  
 此接口的实现都必须进行通信的 Visual Studio 调用[{1>requestmanager](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)编成。 例如，这可以使用消息发布到 DE 的消息处理线程或实现此接口的对象无法保存对 DE 的引用并调用回 DE 与传递到响应`IDebugMessageEvent2::SetResponse`。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 DE 创建并发送此事件对象，以向需要一个响应用户显示一条消息。 通过使用发送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM 附加到正在调试的程序时提供的回调函数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugMessageEvent2`。  
  
|方法|说明|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|获取要显示的消息。|  
|[{1>requestmanager](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|设置响应中，如果有，该消息框中。|  
  
## <a name="remarks"></a>备注  
 如果它要求用户从特定的响应的特定消息，DE 将使用此接口。 例如，如果 DE 尝试远程附加到某个程序之后并获取一条"拒绝访问"消息，DE 此特定将消息发送到 Visual Studio 中的`IDebugMessageEvent2`事件和消息框样式`MB_RETRYCANCEL`。 这允许用户重试或取消附加操作。  
  
 DE 指定通过遵循的约定的 Win32 函数处理此消息的方式`MessageBox`(请参阅[AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)有关的详细信息)。  
  
 使用[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)接口，以将消息发送到 Visual Studio 的不需要对用户进行响应。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
