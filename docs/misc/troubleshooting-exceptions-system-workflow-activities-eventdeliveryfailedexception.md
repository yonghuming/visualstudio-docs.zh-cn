---
title: "关于异常的疑难解答：System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "System.Workflow.Activities.EventDeliveryFailedException 异常"
  - "EventDeliveryFailedException 异常"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Workflow.Activities.EventDeliveryFailedException
当无法向工作流实例发送从宿主引发的事件时，将引发 <xref:System.Workflow.Activities.EventDeliveryFailedException> 异常。 通常，将从工作流实例上的 <xref:System.Workflow.Activities.ExternalDataExchangeService> 引发该事件。 此类不能被继承。  
  
## 备注  
 引发此异常时，会将下列字符串添加到事件日志中：`Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered`。  
  
 使用状态机工作流时，可能会得到显示消息 `Queue '{0}' is not enabled` 的异常。 当状态机的当前状态无法处理特定事件时，将会发生这种情况。 例如，在除当前状态之外的某个状态包含 <xref:System.Workflow.Activities.EventDrivenActivity>（它又包含由 <xref:System.Workflow.Activities.HandleExternalEventActivity> 队列表示的 `'{0}'`）时，将会出现该消息。  
  
## 请参阅  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)