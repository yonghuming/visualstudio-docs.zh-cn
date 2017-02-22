---
title: "CancellationScope 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CancellationScope 活动设计器
**“CancellationScope”**活动设计器用于创建和配置 <xref:System.Activities.Statements.CancellationScope> 活动。  
  
## CancellationScope 活动  
 使用 <xref:System.Activities.Statements.CancellationScope> 活动可指定要执行的活动以及该活动的取消逻辑。  
  
### 使用 CancellationScope 活动设计器  
 **“CancellationScope”**活动设计器可在**“工具箱”**的**“事务”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“CancellationScope”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 CancellationScope 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.Activities.Statements.CancellationScope> 活动。可以在**“CancellationScope”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A> 值。  
  
### CancellationScope 属性  
 下表列出 <xref:System.Activities.Statements.CancellationScope> 属性并说明如何在设计器中使用它们。<xref:System.Activities.Activity.DisplayName%2A> 属性可在属性网格中编辑，但其他属性必须在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 活动的可选友好名称。默认值为 CancellationScope。虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|指定为其提供取消逻辑的活动。若要添加 <xref:System.Activities.Statements.CancellationScope.Body%2A> 活动，请将活动从**“工具箱”**拖放到**“CancellationScope”**活动设计器上带提示文本“在此处放置活动”的**“Body”**框中。|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|指定在取消事件中执行的活动。若要添加 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 活动，请将活动从**“工具箱”**拖放到**“CancellationScope”**活动设计器上带提示文本“在此处放置活动”的**“CancellationHandler”**框中。|  
  
## 请参阅  
 [事务](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)