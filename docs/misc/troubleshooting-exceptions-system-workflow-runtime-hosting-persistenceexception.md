---
title: "关于异常的疑难解答：System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
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
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "PersistenceException 异常"
  - "System.Workflow.Runtime.Hosting.PersistenceException 异常"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Workflow.Runtime.Hosting.PersistenceException
当持久性服务无法满足请求时，将引发 <xref:System.Workflow.Runtime.Hosting.PersistenceException> 异常。  
  
## 备注  
 当 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> 因无法完成请求而不能向其数据库提交完整的范围或工作流实例状态时，将引发 <xref:System.Workflow.Runtime.Hosting.PersistenceException>。  
  
 如果通过从 <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> 类或 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> 类派生来实现持久性服务，则可以引发 <xref:System.Workflow.Runtime.Hosting.PersistenceException> 并显示一条适当的消息，用于指示您的服务所遇到的任何错误条件，这些错误条件会阻止服务完成由工作流运行时引擎发出的请求。  
  
 有关更多信息，请参见<xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>。  
  
## 请参阅  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)