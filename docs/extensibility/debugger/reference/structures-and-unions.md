---
title: "结构和联合 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2fc3225bda24a9ea0d759c1f684801723ea396f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="structures-and-unions"></a>结构和联合
以下是结构和 Visual Studio 调试 SDK 中的联合。  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 指定的进程 ID，这可能是系统 ID 或 GUID。  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 描述将在其下触发断点的条件。  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 描述错误断点，包括位置、 程序和线程的解决方法。  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 指定用于描述断点的位置的结构的类型。  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 定义描述在代码中的一个地址断点的位置的组件。  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 描述直接绑定到被调试的程序中的地址的断点的位置。  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 描述在代码源文件中的行断点的位置。  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 描述在代码中的函数断点的偏移的位置。  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 用于设置基于用户可以输入来自 IDE 的字符串的代码断点。  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 用于设置数据断点基于用户可以输入来自 IDE 的字符串。  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 说明中的特定位置断点的分辨率。  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 描述已通过后将在其触发断点的计数和条件。  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 包含实现断点所需的信息。  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 包含实现断点所需的信息 (与相同[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)结构但包括供应商 GUID、 约束和跟踪点信息)。  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 描述一个代码断点的位置。  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 介绍绑定数据断点的结果。  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 描述一个代码断点或数据断点的断点绑定的信息。  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 指定断点解析位置的结构。  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 描述字符串的数组。  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 指定有关字段类型从元数据中获取信息。  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 描述对函数或方法的调用。  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 描述在其运行调试器的计算机。  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 描述 Guid 列表。  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 描述内存上下文或代码上下文。  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 描述正在调试的程序中的地址。  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 表示一个大量不同类型的地址。  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 标识自定义查看器或键入可视化工具。  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 描述依次进行描述的对象具有名称、 类型和值的层次结构性质的调试属性。  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 描述一个引用。  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 描述到 IDE 以显示反汇编。  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 描述的异常或由正在调试的程序引发的运行时错误。  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 描述本地变量、 参数或其他字段。  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 描述一个堆栈帧。  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 介绍可用的调试引擎的唯一标识符的数组。  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 用于设置模块的 JustMyCode 信息。  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 描述特定计算机。  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 描述在数组内的数组元素。  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 描述类或结构的字段的地址。  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 描述 （通常是一个函数或方法） 的作用域内的局部变量的地址。  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 描述类的方法的地址。  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 描述方法或函数的参数。  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 描述方法或函数的返回的值。  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 描述从元数据中获取的字段类型。  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 描述特定模块 （DLL、 EXE 或程序集）。  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 描述有关都已搜索过的符号搜索路径的状态信息。  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 介绍本机地址。  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 描述 PDB 符号中获取的字段类型。  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 描述的已准备好将绑定到的代码位置的断点的状态。  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 描述的过程。  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 描述的列表[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)对象，表示程序节点。  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 描述在计算机上运行的进程。  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 描述在给定的文本中的行和列位置。  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 介绍在线程的属性。  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 描述字段的类型。  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 描述物理地址。  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 描述相对于地址`this`指针 (`Me`在 Visual Basic 中)。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h、 sh.h 或 ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)