---
title: "IDebugCodeContext2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2
helpviewer_keywords: IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9e003372e390d7e807f314555310c167bf011a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
此接口表示代码指令的起始位置。 为大多数运行时体系结构现在，代码上下文被想象的为程序的执行流中的地址。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎实现此接口可关联到的文档位置代码指令的位置。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 许多接口上的方法返回此接口，最常[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。 它还用于广泛[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)接口以及如下所示断点解析信息。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了上的方法[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)接口，此接口实现以下方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|获取对应于活动的代码上下文文档上下文。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|获取此代码上下文的语言信息。|  
  
## <a name="remarks"></a>备注  
 主要区别`IDebugCodeContext2`接口和[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)接口是`IDebugCodeContext2`始终指令对齐。 这意味着，`IDebugCodeContext2`始终指向指令的开头而`IDebugMemoryContext2`都可能会导致任何字节的内存中的运行时体系结构。 `IDebugCodeContext2`即会递增按说明而不是基本的存储大小 （通常字节）。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)