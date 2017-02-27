---
title: "Parallel 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Parallel 活动设计器
<xref:System.Activities.Statements.Parallel> 活动并发执行一组子活动。  
  
## Parallel 活动  
 <xref:System.Activities.Statements.Parallel> 活动将其子活动存储在 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中。如果某些子活动可能进入空闲状态，则使用 <xref:System.Activities.Statements.Parallel> 活动，而不使用 <xref:System.Activities.Statements.Sequence> 活动。  
  
 <xref:System.Activities.Statements.Parallel> 活动有一个 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 属性，该属性包含用户指定的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 表达式。<xref:System.Activities.Statements.Parallel> 活动在完成每个分支后计算此属性。如果计算结果为 **True**，则 <xref:System.Activities.Statements.Parallel> 活动完成，无需执行其他分支。如果 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 计算结果不为 **True**，则 <xref:System.Activities.Statements.Parallel> 活动在完成其所有子活动后完成。  
  
### 使用 Parallel 活动设计器  
 **“Parallel”**活动设计器可在**“工具箱”**的**“控制流”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左侧的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“Parallel”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动设计器的任何位置，例如，在**“Sequence”**活动设计器内。将该活动设计器放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中之后，它会创建一个 <xref:System.Activities.Statements.Parallel> 活动，该活动默认情况下包含的 <xref:System.Activities.Activity.DisplayName%2A> 为 **Parallel**  
  
 若要向并行活动的 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合添加活动，请将其他活动设计器从**“工具箱”**拖放到**“Parallel”**活动设计器内的三角形上。三角形位于分支中包含的活动的侧面。可通过重复此过程过来添加其他活动。通过在**“Parallel”**活动设计器内拖放活动，可对其重新排序。  
  
### 工作流设计器中的 Parallel 活动属性  
 下表列出 Parallel 活动属性并说明如何在设计器中使用这些属性。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活动设计器在标头中的友好显示名称。默认值为 **Parallel**。可以在**“属性”**网格中编辑该值，或直接在活动设计器标头中编辑该值。|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|包含要执行的子活动的集合。|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|在分支完成后计算。如果其计算结果为 **True**，则取消已安排的挂起的分支。如果未设置此属性或其计算结果为 **False**，则活动在完成其所有子活动后完成。默认值为 **null**。|  
  
## 请参阅  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [控制流](../workflow-designer/control-flow-activity-designers.md)