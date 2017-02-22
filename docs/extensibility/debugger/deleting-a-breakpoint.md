---
title: "删除断点 | Microsoft Docs"
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
  - "删除的断点"
  - "调试 [调试 SDK]，删除断点"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 删除断点
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述进程，在删除挂起的断点时:  
  
## 删除过程  
 会议调试管理器 \(SDM\)调用 [IDebugPendingBreakpoint2:: 删除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 方法从中移除必须挂起的断点和任何绑定断点。  
  
> [!NOTE]
>  一个绑定断点可以通过使用 [IDebugBoundBreakpoint2:: 删除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)的调用中删除。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)