---
title: "PickBranch 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# PickBranch 活动设计器
<xref:System.Activities.Statements.PickBranch> 在可由传入事件触发的 <xref:System.Activities.Statements.Pick> 活动中提供基于事件的执行路径。  
  
## PickBranch  
 <xref:System.Activities.Statements.PickBranch> 对象包含在 <xref:System.Activities.Statements.Pick> 活动的 <xref:System.Activities.Statements.Pick.Branches%2A> 集合中。每个 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活动的一个分支中，并可因某些用作触发器的传入事件而执行。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 由此提供基于事件的控制流建模。每个 <xref:System.Activities.Statements.PickBranch> 都包含一个 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 和一个 <xref:System.Activities.Statements.PickBranch.Action%2A>。  
  
### 如何使用 Pick 活动设计器  
 **“PickBranch”**设计器可在**“工具箱”**的**“控制流”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 当**“Pick”**活动设计器刚放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上时，默认情况下显示名称为**“Branch1”**和**“Branch2”**的两个空 <xref:System.Activities.Statements.PickBranch> 对象会作为 <xref:System.Activities.Statements.Pick> 活动的元素而创建。二者各自的 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 属性值可在**“PickBranch”**设计器标头或每个分支的**“属性”**窗口中进行编辑。  
  
 有两种方法可将 <xref:System.Activities.Statements.PickBranch> 对象添加到 <xref:System.Activities.Statements.Pick> 对象的集合中：从**“工具箱”**拖放**“PickBranch”**设计器，或者使用**“Pick”**设计图面中的上下文菜单：  
  
1.  将**“PickBranch”**设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上**“Pick”**活动设计器的一个分支中时，“PickBranch”活动设计器会创建一个 <xref:System.Activities.Statements.PickBranch>。新 <xref:System.Activities.Statements.PickBranch> 对象可放置在 <xref:System.Activities.Statements.Pick> 设计器内已包含在集合中的任何现有 <xref:System.Activities.Statements.PickBranch> 元素的左侧或右侧。用鼠标将**“PickBranch”**设计器拖到**“Pick”**设计器上时，**“Pick”**设计器会使用一个垂直的蓝灰条来指示在何处添加 <xref:System.Activities.Statements.PickBranch> 以作为给定鼠标放置位置。  
  
2.  右击**“Pick”**活动设计器（但不在**“PickBranch”**设计器内）获取上下文菜单并选择**“创建分支”**以添加一个新的 <xref:System.Activities.Statements.PickBranch>。请注意，新 <xref:System.Activities.Statements.PickBranch> 将添加到**“Pick”**设计器中现有 <xref:System.Activities.Statements.PickBranch> 对象的右侧。  
  
 通过单击**“PickBranch”**设计器标头右侧的双插入符号，可展开该设计器以显示**“触发器”**框和**“操作”**框，还可以通过同样的方法折叠该设计器。编辑每个 <xref:System.Activities.Statements.PickBranch> 的 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 和 <xref:System.Activities.Statements.PickBranch.Action%2A>，方法是将活动放入相应设计器的**“触发器”**和**“操作”**框中。  
  
 通过将 <xref:System.Activities.Statements.Pick> 对象的 <xref:System.Activities.Statements.Pick.Branches%2A> 集合中的 <xref:System.Activities.Statements.PickBranch> 对象拖放到**“Pick”**设计器中的新位置，可将这些对象重新排序。**“Pick”**设计器使用一个垂直的蓝灰条来指示何处作为给定鼠标放置位置而添加 <xref:System.Activities.Statements.PickBranch>。  
  
 有两种方法可删除 <xref:System.Activities.Statements.PickBranch>：  
  
1.  选中**“PickBranch”**设计器并删除它。  
  
2.  选中**“PickBranch”**设计器并右击以获取上下文菜单，然后选择**“删除”**。  
  
 请确保选中**“PickBranch”**设计器，因为若误选该设计器的**“触发器”**或**“操作”**框内的其中一个活动，则会删除这些活动之一，而不是删除 <xref:System.Activities.Statements.PickBranch> 对象。  
  
### 工作流设计器中的 PickBranch 属性  
 下表列出最有用的 <xref:System.Activities.Statements.PickBranch> 属性并说明如何在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|在**“PickBranch”**设计器的标头中显示的友好名称。默认值为 Branch。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|每个 <xref:System.Activities.Statements.PickBranch> 都包含一个可调用 <xref:System.Activities.Statements.PickBranch.Action%2A> 的 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 操作。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|每个 <xref:System.Activities.Statements.PickBranch> 都包含一个触发时将执行的 <xref:System.Activities.Statements.PickBranch.Action%2A>。|  
  
## 请参阅  
 [控制流](../workflow-designer/control-flow-activity-designers.md)   
 [选取活动](../Topic/Pick%20Activity.md)   
 [使用 Pick 活动](../Topic/Using%20the%20Pick%20Activity.md)