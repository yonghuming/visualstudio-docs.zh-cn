---
title: "TerminateWorkflow 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# TerminateWorkflow 活动设计器
**“TerminateWorkflow”**活动设计器用于创建和配置 <xref:System.Activities.Statements.TerminateWorkflow> 活动。  
  
## TerminateWorkflow 活动  
 <xref:System.Activities.Statements.TerminateWorkflow> 活动终止工作流的执行。  
  
### 使用 TerminateWorkflow 活动设计器  
 **“TerminateWorkflow”**活动设计器可在**“工具箱”**的**“运行时”**类别中找到，“工具箱”可通过单击**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具箱”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“TerminateWorkflow”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 TerminateWorkflow 的默认**“DisplayName”**的 <xref:System.Activities.Statements.TerminateWorkflow> 活动。可以在**“TerminateWorkflow”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
### TerminateWorkflow 属性  
 下表列出 <xref:System.Activities.Statements.TerminateWorkflow> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> 活动的友好名称。默认值为 TerminateWorkflow。虽然显示名称不是绝对必需的，但最好使用显示名称。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|终止工作流时要引发的异常。此属性在属性网格中设置。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|解释终止工作流的原因。此属性在属性网格中设置。|  
  
## 请参阅  
 [运行时](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)