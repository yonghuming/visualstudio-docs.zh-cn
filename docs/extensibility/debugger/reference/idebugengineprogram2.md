---
title: "IDebugEngineProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "IDebugEngineProgram2 接口"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口提供多线程调试支持。  
  
## 语法  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎实现此接口支持多个线程同时调试。  此接口在同一对象时实现 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口。  
  
## 调用方的说明  
 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 `IDebugProgram2` 接口的此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugEngineProgram2`方法。  
  
|方法|说明|  
|--------|--------|  
|[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止运行此过程中的所有线程。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|在特定线程注意注意执行\) 的执行 \(或终止。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|在特定允许线程 \(或禁止\) 表达式计算结果，因此，即使程序终止。|  
  
## 备注  
 Visual Studio 会调用此接口以响应 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件和设置程序的 “注意线程步骤”和 “监视线程的表达式计算”状态。  [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 调用，每当程序将停止;此方法将程序有机会停止所有线程。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)