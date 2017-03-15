---
title: "IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
helpviewer_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugInterceptExceptionCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

，当 DE 完成处理带截获的操作时，调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)。  
  
## 语法  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 报告此接口的进程已截获的异常完成。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  
  
## 调用方的说明  
 DE 创建和发送此事件对象报告已截获异常的完成。  事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试的程序。  
  
## 方法按 Vtable 顺序  
 `IDebugInterceptExceptionCompleteEvent2` 接口执行以下操作方法。  
  
|方法|说明|  
|--------|--------|  
|[GetInterceptCookie](../Topic/IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie.md)|返回单个值关联已处理的异常。|  
  
## 备注  
 ，当该方法成功完成处理已截获的异常，此事件将由 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 发送。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)