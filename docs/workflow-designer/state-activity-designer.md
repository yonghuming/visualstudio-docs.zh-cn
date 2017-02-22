---
title: "状态活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "sdanie"
manager: "erikre"
---
# 状态活动设计器
<xref:System.Activities.Statements.State> 表示状态机可具有的状态。  
  
## 使用状态活动设计器  
 要将 <xref:System.Activities.Statements.State> 添加到工作流，请将 **“状态”** 活动设计器从 **“工具箱”** 的 **“状态机”** 部分拖到 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 图面上的 <xref:System.Activities.Statements.StateMachine> 活动。<xref:System.Activities.Statements.State> 活动可以放置到上 <xref:System.Activities.Statements.StateMachine> 和过渡以后；添加或者可以作为创建过渡 <xref:System.Activities.Statements.State> 活动将被删除。若要在一个步骤中添加 <xref:System.Activities.Statements.State> 活动和创建转换，请将**“状态”**活动从**“工具箱”**的**“状态机”**部分拖动，并将鼠标悬停在工作流设计器中的另一状态上。当在另一 <xref:System.Activities.Statements.State> 上拖动了 <xref:System.Activities.Statements.State> 时，四个三角形会出现在 <xref:System.Activities.Statements.State> 周围。如果 <xref:System.Activities.Statements.State> 拖动到其中四个三角形之一，则其将添加到状态机，而且转换将从源 <xref:System.Activities.Statements.State> 创建到放置目标 <xref:System.Activities.Statements.State>。有关更多信息，请参见 [转换](../workflow-designer/transition-activity-designer.md)。  
  
### 工作流设计器中的状态活动属性  
 下表列出可使用工作流设计器的 <xref:System.Activities.Statements.State> 活动属性并说明如何在设计器中使用它们。其中某些属性可以在属性网格中进行编辑，而另一些属性还可以在设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.State> 活动设计器在标头中的友好名称。默认值为 **状态**。可以在属性网格或直接在活动设计器的标头中编辑该值。<xref:System.Activities.Statements.State.DisplayName%2A> 中的工作流设计器顶部显示的痕迹导航使用。<br /><br /> 虽然 <xref:System.Activities.Statements.State.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|在这种状态转换时发生指定的操作。当展开 <xref:System.Activities.Statements.State> 活动，此值可以是集通过拖动从活动 **工具箱** 并拖放到绘图上 **条目** 状态条。|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|在这种状态转换自时发生指定的操作。当展开 <xref:System.Activities.Statements.State> 活动，此值可以是集通过拖动从活动 **工具箱** 并拖放到绘图上 **Exit** 状态条。|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|列出了可能的转换自 <xref:System.Activities.Statements.State>。列表中的每个项有一个指向关联的 <xref:System.Activities.Statements.Transition> 和目标 <xref:System.Activities.Statements.State>。单击此链接将设计器切换到扩展视图的 <xref:System.Activities.Statements.Transition> 或 <xref:System.Activities.Statements.State>。|  
  
## 请参阅  
 [状态机](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [转换](../workflow-designer/transition-activity-designer.md)