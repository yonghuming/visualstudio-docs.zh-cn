---
title: "核心接口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，核心接口"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 核心接口
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

使用 [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]，下面的接口会扩展调试器的核心接口。  
  
## 讨论  
 这些接口主要用于创建调试引擎 \(DE\)。  按类别组织示:  
  
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
  
-   [键入可视化工具](#TypeVisualizers)  
  
 可以实现接口的实体是:  
  
-   调试引擎 \(DE\)  
  
-   端口提供程序 \(PS\)  
  
-   表达式计算器 \(EE\)  
  
-   Visual Studio \(VS\)  
  
##  <a name="Breakpoints"></a> 断点  
 这些接口与实现和跟踪断点相关。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|表示断点绑定到内存位置。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|发送由 DE，当断点绑定到内存位置。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|与|表示断点请求的文档校验和。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|发送由 DE，当断点也可以绑定到内存位置。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|发送由 DE，当断点为止。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|与|表示对断点;使用在创建挂起的断点。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|与|表示对断点;使用在创建挂起的断点。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|表示用于的信息绑定断点。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|发送由 DE，当断点从内存位置为未绑定。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|表示无效断点 \(返回 `IDebugBreakpointErrorEvent2`\)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|表示有关无效断点的分辨率信息。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|表示在断点设置的函数中的位置。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|表示要绑定的断点;使用在创建绑定断点。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|表示中的枚举设置绑定的断点。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|表示中的枚举不能绑定到内存位置中设置断点。|  
  
##  <a name="Contexts"></a> 上下文  
 这些接口表示各种正在调试的程序内的上下文。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|表示代码命令的起始位置。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|扩展 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 接口支持模块检索和处理接口。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|使用， DE|表示文档中的位置。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示计算表达式的上下文。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|一个表示起始位置。记念字节的集合。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示堆栈帧上下文在断点或异常。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示堆栈帧上下文在断点或异常。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|表示中的枚举设置代码上下文。|  
  
##  <a name="CoreServer"></a> 核心服务器  
 这些接口表示程序正在调试的计算机。  这些由 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 实现，但可以调用调试引擎。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|与|提供对端口和端口提供的有关计算机的访问以及信息。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|与|表示支持远程调试的 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 。|  
  
##  <a name="DebugEngines"></a> 调试引擎  
 这些接口表示调试引擎及其关联的事件。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|表示自定义调试引擎。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|表示自定义调试支持符号、 JustMyCode 和异常加载的引擎。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|发送由 DE 的每个新的实例以指示已准备好处理调试任务。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|表示自定义调试支持生成的程序的引擎。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE， PS|表示该程序的节点多个调试引擎的句柄。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|为 SDM 提供了一种获取接口为线程、过程或堆栈帧的调试引擎。|  
  
##  <a name="Documents"></a> 文档  
 这些接口表示文档 \(源文件\) 及其关联的元素。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|发送由 DE 请求文档中打开。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|表示要拆分的指令流从文档的。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|使用， DE|表示 DE 提供的文档，指定名称和类 ID \(CLSID\)。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE， EE|表示调试的校验和文档并允许通过检查和组件之间。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|使用， DE|表示文档上下文，在文档中的一个位置与特定语句和代码上下文相对应。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|使用， DE|表示在文档中的泛型位置。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|与|表示源文件中的位置作为字符偏移量。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|使用， DE|表示文本文档提供 DE \(从派生 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\)，使实际文本。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|发送由 DE 指定要在内存中的源文件。|  
  
##  <a name="Events"></a> 事件  
 这些接口表示发送在、和会话之间调试管理器 \(SDM\)中的所有事件。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|发送由 DE 请求文档中打开。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|在符号加载过程中，调试引擎 \(DE\)发送此接口添加到该会话调试经理 \(SDM\)设置状态栏消息。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|发送由 DE，在程序的一个中断完成。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|发送由 DE，当断点绑定。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|发送由 DE，当断点也可以绑定到。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|发送由 DE，当断点为止。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|发送由 DE，当断点是未绑定。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|发送由 DE 确定是否应在特定位置停止。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|发送由 DE 指定要在内存中的源文件。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|发送由 DE 的每个新的实例以指示已准备好处理调试任务。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|发送由 DE 指示正在调试的程序准备第一个执行命令。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|其他事件接口使用，可以返回错误的接口，提供可读的错误消息。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE， PS|其他事件接口派生的基接口。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|与|表示事件的 SDM 实现的接口 \(是以实现特定的事件接口的对象\) 发送。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|发送由 DE，当异常正在调试的程序发生。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|发送由 DE，在异步表达式计算完成。|  
|IDebugFindSymbolEvent2||过时。  不要使用。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|发送由 DE，在处理已截获异常的已完成。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|发送由 DE，当程序完成加载。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|发送由 DE 具有 IDE 显示一个信息性消息给用户。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|发送由 DE，当模块加载或卸载。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|信号 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 调试器 UI 警告用户符号不能为生成的可执行文件驻留。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|发送由 DE 具有 IDE 显示一个随机字符串。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|使用， DE|发送由端口通信端口事件对任何侦听器。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE， PS|发送由、或端口，进程时创建的。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE， PS|发送由、或端口，当损坏了进程。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE， PS|发送由、或端口，当程序的创建时间。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE， PS|发送由、或端口，当销毁到程序中。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|，在调试会话结束时，可以调试引擎重写 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 的默认行为。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|，当程序的名称更改时，从调试引擎 \(DE\)发送到该会话调试管理器 \(SDM\)。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|发送由 DE，如果新的属性 \(由 `IDebugProperty2` 接口\) 创建的。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|发送由 DE，当销毁了 "。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|发送由 DE，当跳出或函数，因此返回值可以正确显示。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|与|启用调试引擎远程读取指标设置。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|发送由 DE，当一步到，在中，或从命令中完成。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|发送由 DE 指示加载符号的成功或失败模块的。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|发送由 DE，当线程的创建时间。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|发送由 DE，当销毁的线程。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|发送由 DE，当线程已更改其名称。|  
  
##  <a name="Expressions"></a> 表达式  
 这些接口表示在特定上下文将计算的表达式。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|表示要计算的表达式。  从 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口获取。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示计算表达式的上下文。  从 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 接口获取。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|发送由 DE，在异步表达式计算完成。|  
  
##  <a name="Memory"></a> 内存  
 这些接口表示字节序列内存中。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|表示字节序列。可以读取或写入的内存。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示位置。记念字节序列。|  
  
##  <a name="Modules"></a> 模块  
 这些接口表示模块，对应于可执行或 .DLL 文件。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|表示单个可执行文件或 DLL。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|表示支持符号的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|发送由 DE，当模块加载或卸载。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|表示在 PDB 文件包含的源服务器信息。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|表示中的枚举由 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)了解的设置模块。|  
  
##  <a name="Ports"></a> 端口  
 这些接口表示端口和端口提供程序。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|使用， PS|表示本地计算机上的默认端口。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|与|允许使用 DCOM 请求 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 确保的调试引擎，防火墙不会阻止远程调试。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|使用， PS|表示端口。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|发送由端口通信端口事件对任何侦听器。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|表示可生成，并终止进程的端口。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|用于端口注册和注销程序;允许端口跟踪当前正在调试的程序。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|表示选择的端口自定义 UI。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|与|表示对新端口将创建或驻留的端口。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|表示端口的提供程序。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|表示可能仍存在端口的提供程序 \(向磁盘保存\) 有关端口的信息它创建。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|使 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 显示在 **附加的进程** 对话框的 **将信息传输** 部分的内部文本。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|与|查询有关目标计算机的信息允许。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|使用， PS|表示中的枚举将端口。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|与|表示中的枚举将端口提供程序。|  
  
##  <a name="Processes"></a> 进程  
 这些接口表示的过程，包含一个或多个程序的一个可执行。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS， DE|表示正在计算机上运行的进程。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS， DE|表示有效地支持调试的进程 \(用于替换步骤，延续和实现方法在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口\)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE， PS|发送由、或端口，进程时创建的。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE， PS|发送由、或端口，当损坏了进程。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|表示必须跟踪的处理哪个会话附加到它。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|在端口表示枚举设置。|  
  
##  <a name="Programs"></a> 程序  
 这些接口表示程序，不必对应于一个实际可执行文件或模块执行的逻辑单元。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|表示工作所需协力同时调试的其他程序的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE， PS|表示执行一个逻辑单元。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE， PS|发送由、或端口，当程序的创建时间。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE， PS|发送由、或端口，当销毁到程序中。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE， PS|表示可由多个进程调试引擎的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|表示必须能够跟踪的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 哪个会话附加到它。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE， PS|表示可返回有关进程的信息运行它的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE， PS|表示可调试的程序。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE， PS|允许程序节点得到通知尝试附加到关联的程序。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|为 SDM 提供了一种对该 DE 控件的过程查询 DE。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|与|用于使 DES 注册程序提供 SDM 显示其进行调试。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE， PS|表示可包含在线程之间的接口或进程边界的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE， PS|表示枚举设置程序。|  
  
##  <a name="Properties"></a> 属性  
 这些接口表示属性，该属性的值与特定上下文，通常结果表达式计算。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|表示可显示其值以自定义方式的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|表示堆栈帧的值，文档或表达式计算的结果。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|表示随机支持长字符串的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|发送由 DE，如果新的属性 \(由 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 接口\) 创建的。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|发送由 DE，当销毁了 "。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|表示对可在任何特定堆栈帧外显示的属性。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|表示中的枚举设置描述变量、寄存器、参数和表达式的 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|表示中的枚举设置 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构。|  
  
##  <a name="StackFrames"></a> 堆栈帧  
 这些接口表示堆栈帧，断点或发生了异常的上下文。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示断点或发生了异常的上下文。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示可以处理被截取的异常的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|表示中的枚举设置指定函数调用序列用于达到特定堆栈帧的 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) 结构。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|表示中的枚举设置 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构，描述堆栈帧。|  
  
##  <a name="Threads"></a> 线程  
 这些接口表示线程及其关联的事件。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|表示执行线程。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|发送由 DE，当线程的创建时间。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|发送由 DE，当销毁的线程。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|发送由 DE，当线程已更改其名称。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|表示中的枚举设置线程。|  
  
##  <a name="TypeVisualizers"></a> 键入可视化工具  
 这些接口提供类型可视化工具支持。  这些接口由表达式计算器通常实现。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|表示将显示的字节到类型的可视化工具。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|提供用于获取数据访问通过提供方法添加到类型可视化工具。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|表示提供对 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 实现的属性。|  
  
## 请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [创建自定义调试引擎](../../../extensibility/debugger/creating-a-custom-debug-engine.md)