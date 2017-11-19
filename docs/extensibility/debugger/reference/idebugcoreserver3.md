---
title: "IDebugCoreServer3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3
helpviewer_keywords: IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66b543735a48364429eec02d23df0bd08c987035
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
此接口访问的服务器进程正在运行时中的信息。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 Visual Studio 实现此接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 使用[QueryInterface](/cpp/atl/queryinterface)获取此接口从[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)接口。 调用[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)还可以返回此接口。 使用此接口是最常自定义端口供应商来启动程序 （本地或远程） 的服务器上。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了上的方法[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)接口，此接口实现以下方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|检索服务器的名称。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|检索服务器名称的友好版本|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|指示当这些进程启动时自动附加到进程的特定的调试引擎。|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|自动附加失败时，请检索特定错误代码。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|在服务器上创建调试引擎的实例。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|检索一个标志，指示服务器是否在调用方所在的同一计算机上。|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|检索一个值，该值用于与服务器通信的协议。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|禁用所有自动都附加设置此服务器就会了解有关的所有的调试引擎。|  
  
## <a name="remarks"></a>备注  
 自定义端口供应商接收[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)接口上调用[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。 `IDebugCoreServer3`接口可从该接口获取。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)