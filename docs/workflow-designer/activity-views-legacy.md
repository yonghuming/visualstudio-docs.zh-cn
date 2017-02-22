---
title: "活动视图（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "活动, 活动视图"
  - "活动视图"
  - "视图, activity（活动）"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 活动视图（旧版）
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 提供的许多活动（可通过这些活动构成工作流）都具有旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中可用的多个设计视图。将某个活动设计器从**“工具箱”**拖到设计图面上，并且之后每当选择该活动时，都可以通过使用**“工作流”**菜单或通过右击选定的活动在不同设计视图之间切换。同时，当您将指针移到选定活动的名称上时，将出现一组以下拉方式显示的选项卡，可以用来在不同的视图之间切换。  
  
 每个活动都至少有一个视图；此视图是将活动设计器从**“工具箱”**拖到设计图面上时显示的默认视图。此活动默认视图在菜单和选项卡上以**“查看 \[活动类型\]”**选项的形式提供，例如，**“查看 Parallel”**。大多数活动都有附加视图，并且不同活动可以有不同的视图。例如，[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) 活动具有补偿视图，而 [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) 活动具有事件视图。Windows Workflow Foundation 附带的许多活动都有**“查看取消处理程序”**和**“查看错误处理程序”**设计视图，用于查看与活动关联的 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) 和 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)。  
  
 下表列出了每个视图的名称和说明。  
  
|菜单\/选项卡选项|说明|  
|---------------|--------|  
|**查看 \[活动类型\]**|选择此菜单或选项卡选项可查看选定活动的默认图形表示形式。|  
|**查看取消处理程序**|选择此菜单或选项卡选项视图可查看与选定活动关联的 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)。|  
|**查看错误处理程序**|选择此菜单或选项卡选项视图可查看与选定活动关联的 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)。|  
|**查看补偿处理程序**|选择此菜单或选项卡选项视图可查看与选定 [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) 关联的 [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)。|  
|**查看事件处理程序**|选择此菜单或选项卡选项视图可查看与选定 [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) 关联的 [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)。|  
  
 有关类似视图的信息，请参见[顺序工作流视图（旧版）](../workflow-designer/sequential-workflow-views-legacy.md)。  
  
## 请参阅  
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)   
 [顺序工作流视图（旧版）](../workflow-designer/sequential-workflow-views-legacy.md)