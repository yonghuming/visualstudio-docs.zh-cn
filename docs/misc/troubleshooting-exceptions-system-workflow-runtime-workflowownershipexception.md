---
title: "关于异常的疑难解答：System.Workflow.Runtime.WorkflowOwnershipException | Microsoft Docs"
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
  - "EHWRWorkflowOwnership"
helpviewer_keywords: 
  - "System.Workflow.Runtime.WorkflowOwnershipException 异常"
  - "WorkflowOwnershipException 异常"
ms.assetid: 20291283-dfc8-4e34-b84d-f380e04be376
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Workflow.Runtime.WorkflowOwnershipException
当工作流运行时引擎尝试加载当前已由另一个工作流运行时引擎实例加载的工作流实例时，将引发 <xref:System.Workflow.Runtime.WorkflowOwnershipException> 异常。 此外，当在加载工作流时指定的所有权超时时间过期之后，如果工作流运行时引擎尝试保存工作流，也将引发此异常。  
  
## 请参阅  
 <xref:System.Workflow.Runtime.WorkflowOwnershipException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)