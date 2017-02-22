---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "IDebugBreakEvent2 接口"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口一个会话调试管理器 \(SDM\)异步中断已成功完成。  
  
## 语法  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 支持在程序的用户中断的此接口。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同 \(SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口\)。  
  
## 调用方的说明  
 ，当用户请求正在调试的程序暂停时， SDM 调用 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 。  当程序成功暂停时， DE 发送 `IDebugBreakEvent2` 事件。  ，它附加到正在调试的程序，此事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数。  
  
## 备注  
 例如，用户可以在 **调试** 菜单的 **中断任何** 命令运行无限循环的发生程序。  SDM 告诉程序路过调用 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)。  最后，当程序终止时， DE 发送 `IDebugBreakEvent2` 。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)