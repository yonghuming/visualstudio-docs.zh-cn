---
title: "IDebugModule2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2
helpviewer_keywords: IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd8600c592993d24d07add88425e534d5ae99867
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
此接口表示模块-，即一个可执行程序的单元 — （如 DLL)。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口表示一个模块，以便访问有关该模块的信息。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)返回此接口。 DE 发送[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)接口的会话调试管理器 (SDM) 的使用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。  
  
 此接口也可以返回以[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)结构 (通过调用返回的这[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md))。  
  
 [下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)也会返回此接口 ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)返回[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)接口)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugModule2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|获取[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)描述此模块。|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|已过时。 请勿使用。 将重新加载此模块的符号。|  
  
## <a name="remarks"></a>备注  
 模块信息可以显示在**模块**在 IDE 的窗口。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)