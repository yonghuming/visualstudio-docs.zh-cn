---
title: "IDebugCanStopEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2 接口"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口是否在需要会议调试经理 \(SDM\)在当前代码位置停止。  
  
## 语法  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口支持单步执行源代码。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同 \(SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口\)。  
  
 此接口的实现必须将 SDM 调用 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 到调试引擎。  例如，这可以通过传递消息时进行调试引擎的消息处理线程或实现此接口的对象可保存对调试引擎和调用返回具有标志的调试引擎传递给 `IDebugCanStopEvent2::CanStop`。  
  
## 调用方的说明  
 DE 可以发送此方法，每次、请求继续执行，并且、逐句通过代码。  ，它附加到正在调试的程序，此事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugCanStopEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)|获取此事件的原因。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|指定正在调试的程序是否应在该事件的位置停止 \(和发送描述终止的原因\) 的事件或继续执行。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|获取描述此事件的位置的文档上下文。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|获取描述此事件的位置的代码上下文。|  
  
## 备注  
 DE 发送此接口，如果用户单步执行函数，而不是 DE 的外观调试信息存在或调试信息存在，但 DE 不知道源代码是否可以为该位置进行显示。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)