---
title: "Assign 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Assign 活动设计器
**“Assign”**活动设计器用于创建和配置 <xref:System.Activities.Statements.Assign> 活动。  
  
## Assign 活动  
 <xref:System.Activities.Statements.Assign> 活动为变量或参数赋值。  
  
### 使用 Assign 活动设计器  
 **“Assign”**活动设计器可在**“工具箱”**的**“基元”**类别中找到，“工具箱”可通过单击**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具箱”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“Assign”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 Assign 的默认**“DisplayName”**的 <xref:System.Activities.Statements.Assign> 活动。可以在**“Assign”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
### Assign 属性  
 下表列出 <xref:System.Activities.Statements.Assign> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> 活动的友好名称。默认值为 Assign。虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|为其赋 <xref:System.Activities.Statements.Assign.Value%2A> 的变量或参数。它必须是有效的 Visual Basic 标识符。若要设置该属性，请在**“Assign”**活动设计器或属性网格中的**“To”**框中键入 Visual Basic 表达式。|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|赋给变量的值。若要设置 <xref:System.Activities.Statements.Assign.Value%2A>，请在**“Assign”**活动设计器或属性网格中的**“值”**框中键入 Visual Basic 表达式。|  
  
## 请参阅  
 [基元](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)