---
title: "断点错误 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "断点错误"
  - "调试 [调试 SDK]，断点错误"
  - "错误 [调试 SDK]"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 断点错误
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述进程，当断点尝试将代码，但是失败:  
  
## 疑难解答断点错误  
  
1.  调试引擎 \(DE\)发送 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 到该会话调试管理器 \(SDM\)。  
  
2.  SDM 调用 [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(IDebugErrorBreakpoint2 \*\* `ppErrorBP`\) 获取错误断点。  
  
3.  SDM 调用 [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) 获取错误断点给定的挂起的断点。  
  
4.  SDM 调用 [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 获取该项的原因错误断点将不可绑定。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)