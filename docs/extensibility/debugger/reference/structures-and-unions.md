---
title: "结构和联合 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "结构 [Visual Studio SDK]"
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 结构和联合
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

下面是结构和联合在 debugging SDK 的 Visual Studio。  
  
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 指定进程 ID，这可能是系统标识符或 GUID。  
  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 描述断点将激发的条件。  
  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 描述错误断点的解决方案，包括位置、过程和线程。  
  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 指定用于结构的类型描述断点的位置。  
  
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 定义描述断点位置。地址代码中的元素。  
  
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 描述直接绑定到正在调试的程序的地址断点的位置。  
  
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 描述断点位置在行在源代码文件。  
  
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 描述断点的偏移位置。功能在代码。  
  
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 用于设置基于用户可以从 IDE 字符串输入的代码断点。  
  
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 用于设置基于字符串用户可以从 IDE 输入数据断点。  
  
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 在特定位置断点描述的解决方法。  
  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 描述断点将激发的前面之后通过的次数和条件。  
  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 包含要求的信息实现断点。  
  
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 包含要求的信息实现断点 \(和 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 机制相同，但包括供应商 GUID、约束和跟踪点信息\)。  
  
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 描述代码断点的位置。  
  
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 描述绑定数据断点的结果。  
  
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 描述代码断点或数据断点的绑定断点信息。  
  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 指定断点解析位置的结构。  
  
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 描述字符串数组。  
  
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 指定有关从元数据中获取的字段类型的信息。  
  
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)  
 描述调用函数或方法。  
  
 [COMPUTER\_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 描述调试器运行的计算机。  
  
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 描述 GUID 列表。  
  
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)  
 描述一个内存上下文或代码上下文。  
  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 正在调试的过程介绍一个地址。  
  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 表示许多不同的某个地址。  
  
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 标识一个自定义浏览器类型或可视化工具。  
  
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 描述又描述分层性质对象的名称、类型和值的调试属性。  
  
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 描述引用。  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 描述对 IDE 的反汇编显示的。  
  
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 描述程序或运行时错误引发的异常进行调试。  
  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)  
 描述一个局部变量、参数，或其他字段。  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 描述一个堆栈帧。  
  
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 描述数组可用的唯一标识符调试引擎。  
  
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 用于设置模块的 JustMyCode 信息。  
  
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 描述特定计算机。  
  
 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 描述在数组中的一个数组元素。  
  
 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 描述类或结构的域的地址。  
  
 [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 描述一个局部变量的地址在范围内的 \(通常是函数或方法\)。  
  
 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 描述类的方法的地址。  
  
 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 描述方法或函数的参数。  
  
 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 描述从方法或函数的返回值。  
  
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 描述从元数据中获取的一个字段类型。  
  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)  
 描述特定模块 \(DLL、 EXE 或程序集\)。  
  
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 描述有关符号要搜索的搜索路径的状态信息。  
  
 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 描述本机地址。  
  
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 描述从 PDB 符号采取的一个字段类型。  
  
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 描述准备绑定到代码位置断点的状态。  
  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)  
 描述过程。  
  
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 介绍的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 对象列表表示程序节点。  
  
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 描述进程计算机上运行。  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 在给定文本描述行和列位置。  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 描述线程的属性。  
  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)  
 描述一个字段类型。  
  
 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 描述一个物理地址。  
  
 [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 描述相对于 `this` 指针的地址 \(在 Visual Basic 中`Me` \)。  
  
## 要求  
 标题:msdbg.h、 sh.h 或 ee.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)