---
title: "FlowDecision 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb1a9a4781d2ba486f2a9404c2c764a530cdf738
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="flowdecision-activity-designer"></a>FlowDecision 活动设计器
<xref:System.Activities.Statements.FlowDecision> 节点是一个条件节点，它根据指定条件是否成立来将控制流分支到两个备分支之一。 如果流需要的分支超过两个，请改用 <xref:System.Activities.Statements.FlowSwitch%601>。  
  
## <a name="the-flowdecision-node"></a>FlowDecision 节点  
 当流可以分支到两条路径时可使用 <xref:System.Activities.Statements.FlowDecision>。 一个 <xref:System.Activities.Statements.FlowDecision> 节点具有一个 <xref:System.Activities.Statements.FlowDecision.Condition%2A>，并且两个可能结果中的每一个都有一个关联的 <xref:System.Activities.Statements.FlowNode>，这两个可能的结果为：<xref:System.Activities.Statements.FlowDecision.True%2A> 和 <xref:System.Activities.Statements.FlowDecision.False%2A>。 将对 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 进行计算，此计算值决定要在 <xref:System.Activities.Statements.FlowNode> 中处理的下一个 <xref:System.Activities.Statements.Flowchart>。  
  
### <a name="using-the-flowdecision-designer"></a>使用 FlowDecision 设计器  
 **Flowdecision**在找不到设计器**流程图**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **Flowdecision**设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面中**流程图**活动设计器。 这将创建<xref:System.Activities.Statements.FlowDecision>标记为**决策**内<xref:System.Activities.Statements.Flowchart>活动。 鼠标悬停在设计器和**True**和**False**正方形处理框的两个分支显示。  
  
 拖动之后**flowdecision**设计器和其他设计器拖到**流程图**，节点可链接在一起以指定执行顺序。 若要创建的源节点之间的链接 (包括**True**和**False**的分支**flowdecision**) 和目标节点，鼠标悬停在设计器的源节点和它的每一侧显示正方形处理框。 单击这些正方形处理框之一并按下鼠标按钮将其拖到当鼠标悬停在目标节点上时该节点周围以类似方式显示的处理框之一。 松开鼠标按钮，此时将在这两个节点之间创建一个链接，表示为从源设计器指向目标设计器的箭头。  
  
 状态的表达式<xref:System.Activities.Statements.FlowDecision.Condition%2A>可以键入中**条件**框**属性**通过单击的窗口的提示文本显示"输入 VB 表达式"。  
  
### <a name="the-flowdecision-properties"></a>FlowDecision 属性  
 下表列出 <xref:System.Activities.Statements.FlowDecision> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|确定流控制所采用的路径的条件。|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> 成立时流控制所采用的路径。|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> 不成立时流控制所采用的路径。|  
  
## <a name="see-also"></a>另请参阅  
 [流程图](../workflow-designer/flowchart-activity-designers.md)   
 [流程图](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)