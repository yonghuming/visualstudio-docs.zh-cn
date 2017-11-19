---
title: "IDebugBreakpointRequest3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointRequest3
helpviewer_keywords: IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f96bbb9e06b81e648df3d9cd3812d0871c149cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
此接口表示创建并将任何类型的断点绑定需要的信息。 它是扩展的[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 会话调试管理器 (SDM) 通常实现此接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调试引擎 (DE) 访问此接口，通过调用[QueryInterface](/cpp/atl/queryinterface)上对的调用中接收的 IDebugBreakpointRequest2 接口[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)、`IDebugBreakpointRequest3`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|获取描述此断点请求的断点请求信息。|  
  
## <a name="remarks"></a>备注  
 此接口用于向通过 DE 提供其他信息[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)结构。 此附加信息包括 DE 的供应商 ID （以 GUID 形式）、 跟踪点的名称和断点约束的名称。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)