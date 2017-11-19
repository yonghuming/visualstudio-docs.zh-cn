---
title: "IDebugStackFrame3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3
helpviewer_keywords: IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ed100cce9e4677538f12973b6c5586dce0d0548
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
此接口扩展[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)来处理截获的异常。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口上实现的相同对象[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)接口以支持截获的异常。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[QueryInterface](/cpp/atl/queryinterface)上`IDebugStackFrame2`接口，以获得此接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)，`IDebugStackFrame3`公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|处理针对当前堆栈帧之前任何常规异常处理的异常。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|如果出现堆栈展开，则返回代码的上下文。|  
  
## <a name="remarks"></a>备注  
 截获的异常意味着之前由运行时调用任何普通的异常处理例程，调试器可以处理异常。 实质上截获异常意味着使假设是存在，即使没有异常处理程序的运行的时间。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)在普通的异常回调的所有事件过程中调用 (唯一的例外是如果你正在调试混合模式代码 （托管和非托管代码），在这种情况下则无法截获异常期间上一次机会回调）。 如果 DE 不实现`IDebugStackFrame3`，则 DE 从 IDebugStackFrame3 返回一个错误::`InterceptCurrentException` (如`E_NOTIMPL`)，则调试器将正常处理的异常。  
  
 通过截获异常，调试器可以允许用户来对正在调试的程序的状态进行更改，然后继续执行在引发异常的断点。  
  
> [!NOTE]
>  截获允许异常仅在托管代码中，即，运行在公共语言运行时 (CLR) 的程序中。  
  
 调试引擎，它支持通过设置"metricExceptions"截获异常为值 1 在运行时通过使用指示`SetMetric`函数。 有关详细信息，请参阅[SDK 以便进行调试的帮助器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [用于调试的 SDK 帮助程序](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)