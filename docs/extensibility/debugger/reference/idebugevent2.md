---
title: "IDebugEvent2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
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
ms.openlocfilehash: cf76a596a42b166a7e19686ecbae5fe4ddd41ea4
ms.lasthandoff: 04/05/2017

---
# <a name="idebugevent2"></a>IDebugEvent2
此接口用于通信关键的调试信息，例如在断点处停止和非关键的信息，例如调试消息。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 和自定义端口供应商在与所有其他事件接口相同的对象上实现此接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 使用接口 ID (IID) 自变量提供给[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)或[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)，会话调试管理器 (SDM) 调用[QueryInterface](/cpp/atl/queryinterface)上`IDebugEvent2`接口，以获得相应的事件接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|获取此调试事件的属性。|  
  
## <a name="remarks"></a>备注  
 更具体的事件接口，如[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)，不是从 IDebugEvent2 接口，但改为作为与相同的对象上的单独接口实现`IDebugEvent2`。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
