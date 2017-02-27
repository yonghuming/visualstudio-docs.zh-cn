---
title: "命中断点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]、 命中断点"
  - "命中的断点"
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 命中断点
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述进程，在调试引擎 \(DE\)命中断点时，在运行或单步执行时:  
  
## 疑难解答命中断点  
  
1.  DE 发送一 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 接口作为 **EVENT\_SYNC\_STOP**。  
  
2.  会议调试管理器 \(SDM\)调用 [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 获取命中断点。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)