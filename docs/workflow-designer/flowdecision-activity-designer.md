---
title: "FlowDecision 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# FlowDecision 活动设计器
<xref:System.Activities.Statements.FlowDecision> 节点是一个条件节点，它根据指定条件是否成立来将控制流分支到两个备分支之一。如果流需要的分支超过两个，请改用 <xref:System.Activities.Statements.FlowSwitch%601>。  
  
## FlowDecision 节点  
 当流可以分支到两条路径时可使用 <xref:System.Activities.Statements.FlowDecision>。一个 <xref:System.Activities.Statements.FlowDecision> 节点具有一个 <xref:System.Activities.Statements.FlowDecision.Condition%2A>，并且两个可能结果中的每一个都有一个关联的 <xref:System.Activities.Statements.FlowNode>，这两个可能的结果为：<xref:System.Activities.Statements.FlowDecision.True%2A> 和 <xref:System.Activities.Statements.FlowDecision.False%2A>。将对 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 进行计算，此计算值决定要在 <xref:System.Activities.Statements.Flowchart> 中处理的下一个 <xref:System.Activities.Statements.FlowNode>。  
  
### 使用 FlowDecision 设计器  
 **“FlowDecision”**设计器可在**“工具箱”**的**“流程图”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“FlowDecision”**设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上的**“Flowchart”**活动设计器中。这将在 <xref:System.Activities.Statements.Flowchart> 活动中创建一个标记为**“决策”**的 <xref:System.Activities.Statements.FlowDecision>。当鼠标悬停在设计器上时，将出现这两个分支的**“True”**和**“False”**正方形处理框。  
  
 将**“FlowDecision”**设计器和其他设计器拖到**“Flowchart”**之后，这些节点可链接在一起以指定执行顺序。若要在源节点（包括**“FlowDecision”**的**“True”**和**“False”**分支）与目标节点之间创建链接，请将鼠标悬停在源节点的设计器上，此时将在该设计器的每一侧显示正方形处理框。单击这些正方形处理框之一并按下鼠标按钮将其拖到当鼠标悬停在目标节点上时该节点周围以类似方式显示的处理框之一。松开鼠标按钮，此时将在这两个节点之间创建一个链接，表示为从源设计器指向目标设计器的箭头。  
  
 在**“属性”**窗口的**“条件”**框中，单击提示文本“输入 VB 表达式”所在位置即可键入指明 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的表达式。  
  
### FlowDecision 属性  
 下表列出 <xref:System.Activities.Statements.FlowDecision> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中或设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|确定流控制所采用的路径的条件。|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> 成立时流控制所采用的路径。|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> 不成立时流控制所采用的路径。|  
  
## 请参阅  
 [流程图](../workflow-designer/flowchart-activity-designers.md)   
 [流程图](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)