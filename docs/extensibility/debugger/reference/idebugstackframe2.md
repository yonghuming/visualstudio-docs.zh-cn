---
title: "IDebugStackFrame2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2
helpviewer_keywords: IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d7c08cd7fc89e33ef9d505c9e32c23737ef7e84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
此接口表示在特定线程中调用堆栈中的单个堆栈帧。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口来表示一个堆栈帧。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)检索[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)接口。 调用[下一步](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)检索[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)结构，其中包含`IDebugStackFrame2`接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugStackFrame2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|获取此堆栈帧的代码上下文。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|获取此堆栈帧的文档上下文。|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|获取堆栈帧的名称。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|获取堆栈帧的说明。|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|获取依赖于计算机的表示形式与堆栈帧关联的物理地址的范围。|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|获取评估上下文执行的当前上下文中的堆栈帧和线程的表达式计算。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|获取与一个堆栈帧关联的语言。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|获取与一个堆栈帧关联的属性的说明。|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|创建堆栈的枚举数框架属性。|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|获取与一个堆栈帧关联的线程。|  
  
## <a name="remarks"></a>备注  
 仅当正在调试的程序已停止在断点处 （或者由用户设置断点或异常） 时，获取此接口。 从此接口，可以获取表达式上下文来计算表达式，可以返回的寄存器列表，或调用堆栈可以获取和检查。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)