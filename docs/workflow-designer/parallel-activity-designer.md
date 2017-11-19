---
title: "并行活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6b6c0498b98f38b786ce846fd6d975287a2c75e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="parallel-activity-designer"></a>Parallel 活动设计器
<xref:System.Activities.Statements.Parallel> 活动并发执行一组子活动。  
  
## <a name="the-parallel-activity"></a>Parallel 活动  
 <xref:System.Activities.Statements.Parallel> 活动将其子活动存储在 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中。 如果某些子活动可能进入空闲状态，则使用 <xref:System.Activities.Statements.Parallel> 活动，而不使用 <xref:System.Activities.Statements.Sequence> 活动。  
  
 <xref:System.Activities.Statements.Parallel> 活动有一个 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 属性，该属性包含用户指定的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 表达式。 <xref:System.Activities.Statements.Parallel> 活动在完成每个分支后计算此属性。 如果其计算结果为**True**，则<xref:System.Activities.Statements.Parallel>活动完成，无需执行其他分支。 如果<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>的计算结果不**True**，则<xref:System.Activities.Statements.Parallel>活动完成其所有子活动后完成。  
  
### <a name="using-the-parallel-activity-designer"></a>使用 Parallel 活动设计器  
 **并行**在找不到活动设计器**控制流**类别**工具箱**，通过单击访问的哪一**工具箱**的左侧选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **并行**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面活动设计器放置的任何位置通常情况下，例如，内部**序列**活动设计器。 在设计器放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]，它会创建<xref:System.Activities.Statements.Parallel>活动，其中默认情况下包含<xref:System.Activities.Activity.DisplayName%2A>的**并行**  
  
 若要向其中添加活动<xref:System.Activities.Statements.Parallel.Branches%2A>并行活动的集合将一些其他活动设计器从**工具箱**拖放到内的三角形**并行**活动设计器。 三角形位于分支中包含的活动的侧面。 可通过重复此过程过来添加其他活动。 活动可以通过拖放内为这些重新排序**并行**活动设计器。  
  
### <a name="parallel-activity-properties-in-the-workflow-designer"></a>工作流设计器中的 Parallel 活动属性  
 下表列出 Parallel 活动属性并说明如何在设计器中使用这些属性。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活动设计器在标头中的友好显示名称。 默认值是**并行**。 值可以在中根据需要编辑**属性**网格或直接在活动设计器标头。|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|包含要执行的子活动的集合。|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|在分支完成后计算。 如果其计算结果为**True**，然后计划已取消挂起的分支。 如果不设置此属性，或计算结果为**False**，活动完成其所有子活动后完成。 默认值是**null**。|  
  
## <a name="see-also"></a>另请参阅  
 [序列](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [控制流](../workflow-designer/control-flow-activity-designers.md)