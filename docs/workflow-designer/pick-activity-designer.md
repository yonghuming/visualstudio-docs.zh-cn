---
title: "Pick 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Pick 活动设计器
<xref:System.Activities.Statements.Pick> 活动提供基于事件的控制流。该活动执行多个分支中的一个分支来响应某个触发的事件。  
  
## Pick 活动  
 <xref:System.Activities.Statements.Pick> 活动包含一个 <xref:System.Activities.Statements.PickBranch> 对象的集合，<xref:System.Activities.Statements.Pick> 活动会由于某些作为触发器的传入事件而执行其中一个对象。因此，[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供了基于事件的控制流建模。每个 <xref:System.Activities.Statements.PickBranch> 都包含一个 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 和一个 <xref:System.Activities.Statements.PickBranch.Action%2A>。开始执行 <xref:System.Activities.Statements.Pick> 活动时，会安排 <xref:System.Activities.Statements.PickBranch> 元素的所有触发器活动。在第一个活动完成之后，安排其相应的操作活动，并且取消所有其他触发器活动。  
  
### 如何使用 Pick 活动设计器  
 **“Pick”**活动设计器可在**“工具箱”**的**“控制流”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“Pick”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动设计器的任何位置，例如，放置到**“Sequence”**活动设计器内。将该设计器放置到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中之后，它会创建一个 <xref:System.Activities.Statements.Pick> 活动，默认情况下，该活动包含两个空的 <xref:System.Activities.Statements.PickBranch> 活动，作为显示名称为 Branch1 和 Branch2 的元素。二者各自的 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 属性值可在**“PickBranch”**活动设计器标头或每个分支的**“属性”**窗口中编辑。  
  
 有两种方法可将 <xref:System.Activities.Statements.PickBranch> 活动添加到 <xref:System.Activities.Statements.Pick> 对象的集合中：从**“工具箱”**拖放**“PickBranch”**设计器，或者使用**“Pick”**设计图面中的上下文菜单。有关详细信息，请参见 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)主题。请注意，可以放置在**“Pick”**活动设计器中的唯一项为 **“PickBranch”** 活动设计器。  
  
### 工作流设计器中的 Pick 活动属性  
 下表列出 <xref:System.Activities.Statements.Pick> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中或设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Pick> 活动设计器在标头中的友好名称。默认值为 Pick。可以在属性网格或直接在活动设计器的标头中编辑该值。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
  
## 请参阅  
 [控制流](../workflow-designer/control-flow-activity-designers.md)   
 [选取活动](../Topic/Pick%20Activity.md)   
 [使用 Pick 活动](../Topic/Using%20the%20Pick%20Activity.md)