---
title: "IDebugStackFrame3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "IDebugStackFrame3 接口"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口来处理被截取的异常扩展 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 。  
  
## 语法  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现在同一对象的此接口实现支持 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 的接口截获了异常。  
  
## 调用方的说明  
 调用 `IDebugStackFrame2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 除了从 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)继承的方法之外， `IDebugStackFrame3` 显示以下方法。  
  
|方法|说明|  
|--------|--------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|处理当前堆栈帧的异常在任何常规异常处理之前。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|; 如果堆栈展开是发生，返回代码上下文。|  
  
## 备注  
 已截获的异常表示调试器可以处理异常，在所有普通异常处理实例在运行时之前调用。  在运行时的截获的异常表示基本模拟与异常处理程序存在，即使不。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 对所有常规异常回调事件期间 \(此唯一的例外是，如果正在调试混合模式的代码 \(托管和非托管代码\)，因此，在异常无法截获在之前机会回调期间\) 情况下。  如果 DE 不实现 `IDebugStackFrame3`或 DE 返回从 IDebugStackFrame3 的错误::`InterceptCurrentException` \(例如 `E_NOTIMPL`\)，调试器通常将处理异常。  
  
 通过截获异常，调试器可以允许用户对正在调试的程序状态的更改然后继续执行在引发异常的点。  
  
> [!NOTE]
>  被截取的异常在托管代码只允许，即，在运行于公共语言运行时 \(clr\) 下运行的程序 \(CLR\)。  
  
 调试引擎指示使用 `SetMetric` 功能，它通过设置 “metricExceptions”支持截获的异常为值 1 在运行时。  有关更多信息，请参见 [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)