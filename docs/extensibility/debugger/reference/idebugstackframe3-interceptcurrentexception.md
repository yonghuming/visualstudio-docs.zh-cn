---
title: "IDebugStackFrame3::InterceptCurrentException |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords: IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9631f2206705ef6daf36b355aa6cb1d5be6458d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
当它想要截获的当前异常时，由当前的堆栈帧上调试器调用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwFlags`  
 [in]指定不同的操作。 目前，仅[INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)值`IEA_INTERCEPT`支持，并且必须指定。  
  
 `pqwCookie`  
 [out]标识特定异常的唯一值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
 以下是最常见的错误返回。  
  
|错误|描述|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|无法截获当前异常。|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|当前的执行帧尚未尚未搜索处理程序。|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|此框架不支持此方法。|  
  
## <a name="remarks"></a>备注  
 当引发异常时，调试器将从获得控制权在关键点的运行时期间的异常处理过程。 在这些关键时刻，调试器就可以要求当前堆栈帧帧想要截获异常。 这种方式，截获的异常是实质上是即时上异常处理程序的堆栈帧，即使该堆栈帧没有异常处理程序 （例如，在程序代码中一个 try/catch 块）。  
  
 当调试器想要知道是否应截获异常时，将在当前堆栈帧对象上调用此方法。 此方法负责处理的异常的所有详细信息。 如果[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)未实现接口或`InterceptStackException`方法会返回任何错误，则调试器会继续正常处理异常。  
  
> [!NOTE]
>  异常可以截获只能在托管代码中，即被调试的程序下运行时的.NET 运行时。 当然，第三方语言实施者可以实现`InterceptStackException`中如果它们这么选择他们自己的调试引擎。  
  
 截获完成后， [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)处于有信号状态。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)