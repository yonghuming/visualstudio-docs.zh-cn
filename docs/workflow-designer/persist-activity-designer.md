---
title: "Persist 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Persist 活动设计器
**“Persist”**活动设计器用于创建和配置 <xref:System.Activities.Statements.Persist> 活动。  
  
## Persist 活动  
 <xref:System.Activities.Statements.Persist> 活动用于将工作流保存到磁盘中（如有可能）。<xref:System.Activities.Statements.Persist> 活动无法在非持久性区域中执行，例如，在 <xref:System.Activities.Statements.TransactionScope> 活动中。如果在非持久性作用域中使用 <xref:System.Activities.Statements.Persist> 活动，则在运行时会引发异常。  
  
### 使用 Persist 活动设计器  
 **“Persist”**活动设计器可在**“工具箱”**的**“运行时”**类别中找到，“工具箱”可通过单击**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具箱”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“Persist”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 Persist 的默认**“DisplayName”**的 <xref:System.Activities.Statements.Persist> 活动。可以在**“Persist”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
### Persist 属性  
 下表列出 <xref:System.Activities.Statements.Persist> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 活动的友好名称。默认值为持久。虽然显示名称不是绝对必需的，但最好使用显示名称。|  
  
## 请参阅  
 [运行时](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)