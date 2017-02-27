---
title: "TransactionScope 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransactionScope 活动设计器
**“TransactionScope”**活动设计器用于创建和配置 <xref:System.Activities.Statements.TransactionScope> 活动。  
  
## TransactionScope 活动  
 <xref:System.Activities.Statements.TransactionScope> 活动在单个事务中执行所包含的活动。在 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活动以及该事务中的所有其他参与者成功完成时将提交该事务。  
  
### 使用 TransactionScope 活动设计器  
 **“TransactionScope”**活动设计器可在**“工具箱”**的**“事务”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“TransactionScope”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 TransactionScope 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.Activities.Statements.TransactionScope> 活动。可以在**“TransactionScope”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A> 值。  
  
### TransactedReceiveScope 属性  
 下表列出 <xref:System.Activities.Statements.TransactionScope> 属性并说明如何在设计器中使用它们。<xref:System.Activities.Activity.DisplayName%2A> 和 <xref:System.Activities.Statements.TransactionScope.Body%2A> 属性可在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上编辑。但其他属性必须在属性网格上编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TransactionScope> 活动的可选友好名称。默认值为 TransactionScope。虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|指定要在单个事务中执行的活动。若要添加 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活动，请将活动从**“工具箱”**拖放到**“TransactionScope”**活动设计器上带提示文本“在此处放置活动”的**“Body”**框中。|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|指定此 <xref:System.Activities.Statements.TransactionScope> 的 <xref:System.Transactions.IsolationLevel>。|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|指定必须在其间完成事务的时间间隔（格式为 00:00:00，表示小时:分钟:秒）。默认值为 1 分钟 \(00:01:00\)。|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|指定指示在事务中止的情况下是否应中止工作流的值。|  
  
## 请参阅  
 [事务](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)