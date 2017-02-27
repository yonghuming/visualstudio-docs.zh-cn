---
title: "Rethrow 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Rethrow 活动设计器
**“Rethrow”**活动设计器用于创建和配置 <xref:System.Activities.Statements.Rethrow> 活动。  
  
## Rethrow 活动  
 <xref:System.Activities.Statements.Rethrow> 活动引发先前已引发的异常。此活动只能在 <xref:System.Activities.Statements.TryCatch> 活动的 <xref:System.Activities.Statements.Catch> 处理程序中使用。  
  
### 使用 ReThrow 活动设计器  
 **“ReThrow”**活动设计器可在**“工具箱”**的**“错误处理”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左侧的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“Rethrow”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 Throw 的默认**“DisplayName”**的 <xref:System.Activities.Statements.Rethrow> 活动。可以在**“Rethrow”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A> 值。  
  
### Rethrow 属性  
 下表列出 <xref:System.Activities.Statements.Rethrow> 属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.ReThrow> 活动的可选友好名称。默认值为 Rethrow。|  
  
## 请参阅  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)