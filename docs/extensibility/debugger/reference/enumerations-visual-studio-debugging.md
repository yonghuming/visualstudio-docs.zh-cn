---
title: "枚举 (Visual Studio 调试) | Microsoft Docs"
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
  - "枚举 [Visual Studio SDK]"
  - "调试 [调试 SDK] 枚举"
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 枚举 (Visual Studio 调试)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

以下 debugging SDK 的 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 的枚举。  
  
 [AD\_PROCESS\_ID\_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)  
 指定如何解释在 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) 结构的进程 ID。  
  
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)  
 指定地址的类型。  
  
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)  
 指定的位置程序集。  
  
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)  
 指定其原因以便调试引擎 \(DE\)可以附加到程序节点。  
  
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)  
 为挂起和绑定断点指定断点条件样式。  
  
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)  
 指定断点的错误类型。  
  
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)  
 提供可用于指定附加信息，当设置断点时的可选标志。  
  
 [BP\_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md)  
 枚举能用于指定附加信息，当设置断点时的可选标志的有效值。  此枚举扩展 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 枚举。  
  
 [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)  
 为断点指定请求断点位置类型。  
  
 [BP\_PASSCOUNT\_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)  
 指定条件与将导致断点激发的断点通过计数。  
  
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)  
 指定数据断点是否在硬件模拟或实现。  
  
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)  
 指定绑定断点的存在，并且它是否启用。  
  
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)  
 指定断点是否在代码位置，即数据位置或者是另一个断点。  
  
 [BP\_UNBOUND\_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md)  
 将断点是未绑定的原因。  
  
 [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)  
 指定检索的信息有关断点的一个失败的解决方法。  
  
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)  
 指定检索的信息有关断点请求。  
  
 [BPREQI\_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md)  
 枚举指定要检索的信息有关断点请求的有效值。  此枚举扩展 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 枚举。  
  
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)  
 指定信息将检索有关断点的成功解决。  
  
 [CANSTOP\_REASON](../../../extensibility/debugger/reference/canstop-reason.md)  
 用于确定程序是否可以在到达特定之后终止执行点在执行。  
  
 [CONNECTION\_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)  
 指示使用的协议通信在调试服务器和调试包之间的值。  
  
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)  
 选择构造函数具有不同的类型。  
  
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)  
 用于比较两个内存上下文指定条件。  
  
 [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)  
 指定检索的信息有关内存上下文。  
  
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)  
 描述 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 或 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 接口的各个属性。  
  
 [DEBUG\_REASON](../../../extensibility/debugger/reference/debug-reason.md)  
 指定进程的原因。调试生成。  
  
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)  
 指定检索的信息有关调试属性对象。  
  
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)  
 指定检索的信息有关调试引用对象。  
  
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)  
 用于反汇编指定标志。  
  
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)  
 指定检索的信息有关反汇编字段。  
  
 [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)  
 指定反汇编流的大小。  
  
 [DisplayKind](../../../extensibility/debugger/reference/displaykind.md)  
 枚举表示该信息来自接受一个 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象和向用户显示的有效值。  
  
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)  
 用于比较两个指定标准文档上下文。  
  
 [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)  
 指定要对转储的过程状态。  
  
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)  
 指定如何解释 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象的类型。  
  
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)  
 表示编辑器的原因，并继续 " 不可用。  
  
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)  
 指定控制表达式计算的标志。  
  
 [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md)  
 枚举控制表达式计算的标志的有效值。  此枚举扩展 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 枚举。  
  
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)  
 指定事件属性。  
  
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)  
 指定异常状态。  
  
 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)  
 指定检索的信息有关 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象。  
  
 [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md)  
 指定在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象的字段包含的。  
  
 [FIELD\_KIND\_EX](../../../extensibility/debugger/reference/field-kind-ex.md)  
 枚举 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象可以包含的其他类型字段。  此枚举扩展 [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) 枚举。  
  
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)  
 为字段类型指定修饰符。  
  
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)  
 指定信息以检索堆栈帧对象。  
  
 [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)  
 指定主机名的类型。  
  
 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)  
 指定文件的名称类型检索。  
  
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)  
 指定使用哪些操作，当截获异常时。  
  
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)  
 指定程序将如何生成。  
  
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)  
 指定检索哪种信息为特定设备。  
  
 [MACHINE\_INFO\_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)  
 用于描述计算机。  
  
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)  
 指定消息类型及其原因。  
  
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)  
 用于描述模块。  
  
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)  
 指定标志对于调试模块信息。  
  
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)  
 为模块指定符号状态。  
  
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)  
 在匹配名称选择用例选项。  
  
 [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md)  
 指定一个对象的类型从表达式计算器。  
  
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)  
 指定如何分析表达式。  
  
 [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)  
 指定挂起的断点 \(尚未绑定\) 的断点状态。  
  
 [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)  
 指定挂起状态断点标志。  
  
 [PORT\_SUPPLIER\_DESCRIPTION\_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md)  
 定义可以检索有关端口提供程序的元数据。  
  
 [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)  
 指定了检索哪种信息进程。  
  
 [PROCESS\_INFO\_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)  
 描述或指定进程的属性。  
  
 [PROGRAM\_DESTROY\_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)  
 枚举程序的有效值销毁标志。  
  
 [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)  
 指定特性与程序提供程序。  
  
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)  
 指定希望从程序提供程序将获取的属性。  
  
 [REFERENCE\_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)  
 指定比较的类型为引用。  
  
 [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)  
 指定引用类型。  
  
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)  
 指定开始查找 " 反汇编的位置。  
  
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)  
 对单步执行指定步骤类型。  
  
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)  
 对单步执行指定步骤单元。  
  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)  
 指定检索哪种符号信息。  
  
 [TEXT\_DOC\_ATTR\_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)  
 描述文档的属性。  
  
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)  
 指定要检索的线程的信息。  
  
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)  
 指定线程的状态。  
  
## 要求  
 标题:msdbg.h、 sh.h 或 ee.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)