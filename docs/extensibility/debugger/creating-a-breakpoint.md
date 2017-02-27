---
title: "创建一个断点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "创建的断点"
  - "调试 [调试 SDK]，创建断点"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 创建一个断点
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述创建断点处理。  
  
## 在断点上创建的方法  
 当需要的绑定断点时的模块加载，该会话调试管理器 \(SDM\)调用下列方法:  
  
1.  [IDebugPendingBreakpoint2:: 启用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2:: 活动](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  ，只有当用户在 " 断点 " 窗口时，对断点**CanBind** 调用。  
  
4.  [IDebugPendingBreakpoint2:: 绑定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)