---
title: "IDebugProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2"
helpviewer_keywords: 
  - "IDebugProgram2 接口"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示进程中运行的程序。  
  
## 语法  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)和自定义端口提供程序实现此接口表示进程中的程序。  会议调试管理器 \(SDM\)还实现此接口提供信息 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。  
  
## 调用方的说明  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件返回一个新过程的此接口。  此接口还用作参数为多个接口中的许多方法。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProgram2`方法。  
  
|方法|说明|  
|--------|--------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|枚举在此过程中运行的线程。|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|获取程序的名称。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|获取此过程运行的进程。|  
|[终止](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|停止此过程。|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|附加到此过程。|  
|[CanDetach](../Topic/IDebugProgram2::CanDetach.md)|确定调试引擎 \(DE\)是否能从程序分离。|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|分离此过程的调试器。|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|获取此过程的全局唯一标识符 \(guid\)。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|获取程序特性。|  
|[执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|继续运行从一种停止状态的此过程。  清除所有以前执行状态。|  
|[继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|继续运行从一种停止状态的此过程。  所有以前执行状态保留。|  
|[单步执行](../../../extensibility/debugger/reference/idebugprogram2-step.md)|执行一步。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|请求此过程停止其线程的执行一次运行代码。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|获取运行此程序的调试引擎的名称 \(DE\)和标识符。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|枚举特定位置的代码上下文在源文件中。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|获取此过程的内存中字节数组。|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|获取此过程将程序或部分的反汇编流。|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|此枚举程序已加载的模块和执行。|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|获取编辑并继续 " \(此过程的 ENC\) 更新。<br /><br /> 自定义调试引擎不执行此方法 \(它应始终返回 `E_NOTIMPL`\)。|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|此枚举程序代码路径。|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|写入文件的转储。|  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 备注  
 ，而过程由一个或多个程序组成，程序是运行在特定运行时结构中的线程容器。  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [下一步](../Topic/IEnumDebugPrograms2::Next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)