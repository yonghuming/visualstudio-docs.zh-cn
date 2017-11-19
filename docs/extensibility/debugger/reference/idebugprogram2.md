---
title: "IDebugProgram2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2
helpviewer_keywords: IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 754b2e79131e425b8e27c0084acbd6243016815a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2"></a>IDebugProgram2
此接口表示进程中运行的程序。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 和自定义端口提供程序实现此接口来表示进程中的程序。 会话调试管理器 (SDM) 还可实现此接口将信息提供给[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件返回的新程序此接口。 此接口还用于对多个接口的许多方法使用作为参数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugProgram2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|枚举在此程序中运行的线程。|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|获取该程序的名称。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|获取此程序在运行时的进程。|  
|[终止](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|终止此程序。|  
|[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|将附加到此程序。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|确定是否调试引擎 (DE) 可以从程序中分离。|  
|[分离](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|将此程序从调试器分离。|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|获取此程序的全局唯一标识符。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|获取程序属性。|  
|[执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|将继续从停止的状态运行此程序。 清除任何以前的执行状态。|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|将继续从停止的状态运行此程序。 将保留任何以前的执行状态。|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|执行一个步骤。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|此程序停止执行下一步的请求的时间其线程运行代码之一。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|获取的名称和运行此程序的调试引擎 (DE) 的标识符。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|枚举给定位置在源文件中的代码上下文。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|获取此程序的内存字节数。|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|获取此程序或此计划的一部分的反汇编流。|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|枚举该程序已加载，并且正在执行的模块。|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|获取此程序的编辑并继续 (ENC) 更新。<br /><br /> 自定义调试引擎不实现此方法 (它应始终返回`E_NOTIMPL`)。|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|枚举该程序的代码路径。|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|转储写入文件。|  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>备注  
 程序是在特定的运行时体系结构中，运行，而进程组成一个或多个程序的线程容器。  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)