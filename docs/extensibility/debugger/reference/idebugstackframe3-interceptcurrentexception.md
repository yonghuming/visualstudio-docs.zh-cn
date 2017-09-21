---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调用由当前堆栈帧的调试器，则若要截获当前异常。  
  
## 语法  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### 参数  
 `dwFlags`  
 \[in\] 指定不同的操作。  目前，仅 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) 值 `IEA_INTERCEPT` 支持并且必须指定。  
  
 `pqwCookie`  
 \[out\] 标识特定异常的唯一值。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
 下面是最常见的错误返回。  
  
|错误|说明|  
|--------|--------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|无法截获当前异常。|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|当前执行帧尚未搜索处理程序。|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|此方法不受此框架支持。|  
  
## 备注  
 引发异常时，控件从的运行时关键点在异常处理过程的调试器的进程。  在这些关键时间期间，因此，如果帧若要截获异常，调试器可能需要当前堆栈帧。  这样，已截获的异常实质上是堆栈帧的一个正在进行中的异常处理程序，因此，即使该堆栈帧没有异常处理程序 \(例如， try\/catch 在程序代码块\)。  
  
 当调试器需要知道是否应截获异常，则调用当前堆栈帧对象的方法。  此方法以处理异常的所有详细信息负责。  如果 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) 接口未实现或 `InterceptStackException` 方法返回所有错误，则调试器继续正常处理异常。  
  
> [!NOTE]
>  ，当正在调试的程序运行在 .NET 运行时下，即，第二次异常仅可被截获。  当然，因此，如果他们这样做选择，第三方语言实现可以实现在其 `InterceptStackException` 调试引擎。  
  
 在截获完成后， [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) 终止状态。  
  
## 请参阅  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)