---
title: "Compensate 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Compensate.UI"
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Compensate 活动设计器
**“Compensate”**活动设计器用于创建和配置 <xref:System.Activities.Statements.Compensate> 活动。  
  
## Compensate 活动  
 <xref:System.Activities.Statements.Compensate> 活动为 <xref:System.Activities.Statements.CompensableActivity> 中包含的活动显式调用 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>。如果 <xref:System.Activities.Statements.Compensate> 活动未在 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 中使用，则必须指定 <xref:System.Activities.Statements.Compensate.Target%2A> 属性。  
  
 由 <xref:System.Activities.Statements.Compensate.Target%2A> 指定的 <xref:System.Activities.Statements.CompensationToken> 提供了在 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 成功完成之后显式确认或补偿 <xref:System.Activities.Statements.CompensableActivity> 的方法。  
  
### 使用 Compensate 活动设计器  
 **“Compensate”**活动设计器可在**“工具箱”**的**“事务”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左侧的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“Compensate”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 Compensate 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.Activities.Statements.Compensate> 活动。可以在**“Compensate”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A> 值。  
  
### Compensate 属性  
 下表列出 <xref:System.Activities.Statements.CancellationScope> 属性并说明如何在设计器中使用它们。<xref:System.Activities.Activity.DisplayName%2A> 属性可在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑，但 <xref:System.Activities.Statements.Compensate.Target%2A> 属性必须在属性网格中编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Compensate> 活动的可选友好名称。默认值为 Compensate。|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|指定 <xref:System.Activities.InArgument%601>，它包含此 <xref:System.Activities.Statements.Compensate> 活动的 <xref:System.Activities.Statements.CompensationToken>。|  
  
## 请参阅  
 [事务](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate Activity Designer](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)