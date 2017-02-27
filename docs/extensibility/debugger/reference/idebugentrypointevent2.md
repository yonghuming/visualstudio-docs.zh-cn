---
title: "IDebugEntryPointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEntryPointEvent2"
helpviewer_keywords: 
  - "IDebugEntryPointEvent2 接口"
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

，当程序将执行其用户代码的第一命令时，调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)。  
  
## 语法  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 作为其行为的一部分此接口。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  
  
## 调用方的说明  
 DE 创建和发送此事件对象，而正在调试的程序加载时和准备执行用户代码的第一命令。  事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试的程序。  
  
## 备注  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ，当程序将首先执行一个命令时，发送。  例如， `IDebugEntryPoint2` ，当程序将对用户的 `main` 函数时，发送。  
  
 当 DE 发送 `IDebugEntryPointEvent2`时，当前代码位置应在用户代码中第一个命令，如 `main`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)