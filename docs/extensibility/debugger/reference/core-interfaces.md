---
title: "核心接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 367917032b836ce6a7d07cf3eba85db14464a957
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="core-interfaces"></a>核心接口
下列接口是用于通过扩展调试器的核心接口[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]。  
  
## <a name="discussion"></a>讨论  
 这些接口主要用于创建的调试引擎 (DE)。 它们此处按类别进行组织：  
  
-   [断点](#Breakpoints)  
  
-   [上下文](#Contexts)  
  
-   [核心服务器](#CoreServer)  
  
-   [调试引擎](#DebugEngines)  
  
-   [文档](#Documents)  
  
-   [事件](#Events)  
  
-   [表达式](#Expressions)  
  
-   [内存](#Memory)  
  
-   [模块](#Modules)  
  
-   [端口](#Ports)  
  
-   [进程](#Processes)  
  
-   [程序](#Programs)  
  
-   [属性](#Properties)  
  
-   [堆栈帧](#StackFrames)  
  
-   [线程](#Threads)  
  
-   [类型可视化工具](#TypeVisualizers)  
  
 可以实现接口的实体是：  
  
-   调试引擎 (DE)  
  
-   端口供应商 (PS)  
  
-   表达式计算器 (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a>断点  
 相关这些接口的实现和跟踪断点。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|表示一个绑定到的内存位置的断点。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|断点绑定到的内存位置时，由 DE 发送。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|表示断点请求的文档校验和。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|断点无法绑定到的内存位置时，由 DE 发送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|当到达断点时，由 DE 发送。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|表示断点; 的请求用于创建挂起断点。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|表示断点; 的请求用于创建挂起断点。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|表示用于绑定的断点的信息。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|当从内存位置断点是未绑定由 DE 发送。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|表示无效的断点 (返回`IDebugBreakpointErrorEvent2`)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|表示有关无效的断点的解决方法信息。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|表示在函数中设置了断点的位置。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|表示要绑定; 一个断点用于创建绑定的断点。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|通过一组绑定断点表示枚举。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|通过一组无法绑定到的内存位置的断点表示枚举。|  
  
##  <a name="Contexts"></a>上下文  
 这些接口表示各种类型的上下文内被调试的程序。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|表示代码指令的起始位置。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|扩展[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)接口要启用的模块和过程接口检索。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|表示在文档中的位置。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示在其中计算的表达式的上下文。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示在内存中的字节组成的集合的起始位置。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示在断点或异常的堆栈帧上下文。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示在断点或异常的堆栈帧上下文。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|表示在代码的上下文中的某一集合的枚举。|  
  
##  <a name="CoreServer"></a>核心服务器  
 这些接口表示正在其调试程序的计算机。 这些功能通过实现[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]，但可以为调用的调试引擎。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|提供对端口和端口供应商，以及有关计算机的信息的访问。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|表示[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)支持远程调试。|  
  
##  <a name="DebugEngines"></a>调试引擎  
 这些接口表示的调试引擎和及其关联的事件。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|表示自定义调试引擎。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|表示支持加载符号、 JustMyCode 和异常的自定义调试引擎。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|发送的每个 DE 的新实例，以指示它已准备好处理调试任务。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|表示支持启动的程序的自定义调试引擎。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|表示处理多个调试引擎的程序节点。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|提供 SDM 接口获得的调试引擎从线程、 程序或堆栈帧的方法。|  
  
##  <a name="Documents"></a>文档  
 这些接口表示文档 （源文件） 和其关联的元素。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|由 DE 发送，以请求要打开的文档。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|表示从文档的反汇编指令的流。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS DE|表示由 DE，指定名称和 ID (CLSID) 的类提供的文档。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE EE|表示调试文档的校验和，并可将组件之间传递校验和。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|表示文档上下文中，对应于特定语句和代码上下文文档内的位置。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS DE|表示在文档内的常规位置。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|表示为字符偏移量在源文件中的位置。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS DE|表示由 DE 提供一个文本文档 (派生自[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md))，提供的实际文本。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|由 DE 发送，以指定对内存中的源文件的更改。|  
  
##  <a name="Events"></a> 事件  
 这些接口表示 DE 和会话调试管理器 (SDM) 之间发送的所有事件。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|由 DE 发送，以请求要打开的文档。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|调试引擎 (DE) 期间将发送此接口到会话调试管理器 (SDM) 的状态设置栏上的消息符号加载。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|完成程序中的出现中断时，由 DE 发送。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|当绑定断点时，由 DE 发送。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|由 DE 断点绑定失败时发送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|当到达断点时，由 DE 发送。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|未绑定断点时，由 DE 发送。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|由 DE 发送，以确定它是否应停止的特定位置。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|由 DE 发送，以指定对内存中的源文件的更改。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|发送的每个 DE 的新实例，以指示它已准备好处理调试任务。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|由 DE 发送，以指明被调试的程序尚未准备好执行的第一个指令。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|一个接口，由其他事件接口，这样可能会返回错误，以便提供用户可读错误消息。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE PS|接口派生自的所有其他事件的基接口。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|表示由 （表示为实现特定的事件接口的对象） 的事件发送到 SDM 实现的接口。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|当正在调试的程序中出现了异常由 DE 发送。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|由 DE 异步表达式求值完成后发送。|  
|IDebugFindSymbolEvent2||已过时。 请勿使用。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|由 DE 截获异常的处理已完成时发送。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|在程序完成加载时由 DE 发送。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|由发送 DE 能够 IDE 显示一条信息性消息给用户。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|加载或卸载模块时，由 DE 发送。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|信号[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]调试器用户界面以警告符号不找不到启动可执行文件的用户。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|由 DE 能够 IDE 显示发送一个任意字符串。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS DE|发送端口进行通信的任何侦听器端口事件。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|创建一个进程时发送 DE 或端口。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|进程已销毁时发送 DE 或端口。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|由 DE 或端口创建的程序时发送。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|程序已销毁时发送 DE 或端口。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|允许重写默认行为的调试引擎[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 时结束调试会话。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|从发送的调试引擎 (DE) 到会话调试管理器 (SDM) 程序的名称更改时。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|发送 DE 时新的属性 (由表示`IDebugProperty2`接口) 已创建。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|属性已销毁时，由 DE 发送。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|在逐句外或过程执行函数，以便可以正确显示返回的值时，由 DE 发送。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|启用调试引擎读取指标设置远程。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|由 DE 到、 逐过程执行或跳出指令的步骤完成后发送。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|由 DE 发送，以指明是成功还是失败的加载的模块的符号。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在创建线程时，由 DE 发送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|销毁线程时，由 DE 发送。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|当一个线程已更改其名称由 DE 发送。|  
  
##  <a name="Expressions"></a>表达式  
 这些接口表示要在特定上下文中计算表达式。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|表示要进行求值的表达式。 从获取[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示表达式的计算的上下文。 从获取[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)接口。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|由 DE 异步表达式求值完成后发送。|  
  
##  <a name="Memory"></a>内存  
 这些接口表示内存中的字节序列。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|表示一个可以读取或写入到的内存中的字节序列。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示序列的内存中的字节的位置。|  
  
##  <a name="Modules"></a> 模块  
 这些接口表示一个对应的可执行文件的模块或。DLL 文件。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|表示单个可执行文件或 DLL。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|表示[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)支持符号。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|加载或卸载模块时，由 DE 发送。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|表示 PDB 文件中包含的源服务器信息。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|通过一组模块的已知表示枚举[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)。|  
  
##  <a name="Ports"></a>端口  
 这些接口表示端口和端口供应商。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS PS|表示本地计算机上的默认端口。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|启用调试引擎，使用 DCOM 询问[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI，以确保该防火墙将阻止远程调试。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS PS|表示的端口。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|发送端口进行通信的任何侦听器端口事件。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|表示可以启动和终止进程的端口。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|用于注册和注销程序使用端口;允许要跟踪当前正在调试的程序的端口。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|表示自定义的 UI 选择端口。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|表示从中创建或位于一个新的端口的端口的请求。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|表示的供应商提供的端口。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|表示可以保留的端口的供应商 （保存到磁盘） 的端口信息创建它。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|使[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI，以显示内的文本**传输信息**部分**附加到进程**对话框。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|允许对目标计算机有关的信息的查询。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS PS|通过一组的端口表示枚举。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|表示在某一端口供应商提供的集合的枚举。|  
  
##  <a name="Processes"></a>进程  
 这些接口表示进程，包含一个或多个程序的单个可执行文件。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS，DE|表示在计算机运行的进程。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS，DE|表示当前支持的进程调试 (用于替换步骤，继续，并在执行方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)接口)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|创建一个进程时发送 DE 或端口。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|进程已销毁时发送 DE 或端口。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|表示必须跟踪会话附加到它的进程。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|表示一组在端口上的进程的枚举。|  
  
##  <a name="Programs"></a>程序  
 这些接口表示程序，并不一定对应于物理可执行文件或模块的逻辑单元的执行。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|表示[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)需要在同一时间正在调试其他程序协同工作。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE PS|表示执行一个逻辑单元。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|由 DE 或端口创建的程序时发送。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|程序已销毁时发送 DE 或端口。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|表示[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可以由多个调试引擎。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|表示[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)它必须能够跟踪会话附加到它。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE PS|表示[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，可返回有关在其中运行的过程的信息。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE PS|表示可调试的程序。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE PS|允许接收通知的尝试将附加到关联的程序的程序节点。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|提供一种方法来查询有关由该 DE 控制的程序 DE SDM。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|由 DEs 用于注册 SDM 以显示正在调试的程序。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE PS|表示[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可以跨线程或进程边界封送接口。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE PS|表示程序集的枚举。|  
  
##  <a name="Properties"></a>属性  
 这些接口表示属性，与特定的上下文，通常的表达式计算结果关联的值。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|表示[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，可以自定义方式显示其值。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|表示一个堆栈帧、 文档或的表达式计算结果的值。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|表示[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)支持任意长字符串。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|发送 DE 时新的属性 (由表示[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)接口) 已创建。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|属性已销毁时，由 DE 发送。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|表示一个属性，它可以存在于任何特定堆栈帧外部的引用。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|通过一组表示枚举[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)结构用于描述变量、 寄存器、 参数和表达式。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|通过一组表示枚举[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)结构。|  
  
##  <a name="StackFrames"></a>堆栈帧  
 这些接口表示一个堆栈帧，上下文断点或异常已发生。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示上下文断点或异常已发生。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)其可以处理截获异常。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|表示访问集合的枚举[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)结构指定函数调用用于到达特定堆栈帧的序列。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|通过一组表示枚举[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)结构，用于描述堆栈帧。|  
  
##  <a name="Threads"></a>线程  
 这些接口表示线程和及其关联的事件。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|表示执行的线程。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在创建线程时，由 DE 发送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|销毁线程时，由 DE 发送。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|当一个线程已更改其名称由 DE 发送。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|表示在线程某一集合的枚举。|  
  
##  <a name="TypeVisualizers"></a>类型可视化工具  
 这些接口为类型可视化工具提供支持。 由表达式计算器，通常会实现这些接口。  
  
|接口|由实现|描述|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|表示要将其提交到类型可视化工具的字节数组。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|提供用于获取对要传递给类型可视化工具的数据的访问方法。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|表示一个属性，提供对访问[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)实现。|  
  
## <a name="see-also"></a>另请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [创建自定义调试引擎](../../../extensibility/debugger/creating-a-custom-debug-engine.md)