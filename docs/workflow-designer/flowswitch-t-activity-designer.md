---
title: "FlowSwitch&lt;T&gt;活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 264ad0b02d2b352de69a84101b967ae6e663c422
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt;活动设计器
<xref:System.Activities.Statements.FlowSwitch%601> 活动是一个条件节点，它在需要两个以上备选分支时根据匹配条件分支控制流。 如果流分支仅需要两个路径，请改用 <xref:System.Activities.Statements.FlowDecision> 活动。  
  
## <a name="the-flowswitcht-activity"></a>FlowSwitch < T\>活动  
 <xref:System.Activities.Statements.FlowSwitch%601>活动包含<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>返回类型的值*T* （由泛型参数指定） 评估时。 该活动还包含一组 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>，它指定从此计算的可能结果到一组 <xref:System.Activities.Statements.FlowNode> 对象的唯一映射。 <xref:System.Activities.Statements.FlowNode>执行的对象的类型是一个*T*是计算得到的值相匹配<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>。 可以选择在没有获得任何匹配时提供 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> Case。  
  
### <a name="using-the-flowswitcht-activity-designer"></a>使用 FlowSwitch\<T > 活动设计器  
 **FlowSwitch\<T >**在找不到活动设计器**流程图**类别**工具箱**，通过单击访问的哪一**工具箱**的左侧选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **FlowSwitch\<T >**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面中**流程图**活动设计器。 使用**选择类型**窗口，其中显示指定的类型 (在代码中使用关联<xref:System.Activities.Statements.FlowSwitch%601>通过其泛型参数) 从评估中获得<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>。 此过程创建<xref:System.Activities.Statements.FlowSwitch%601>活动标记为**交换机**内<xref:System.Activities.Statements.Flowchart>活动。 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>可以键入中**表达式**框**属性**通过单击的窗口的提示文本显示"输入 VB 表达式"。  
  
 将鼠标移到**FlowSwitch\<T >**活动设计器会导致用于链接的正方形处理<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>其边缘周围出现。 拖动之后**FlowSwitch < T\>** 活动设计器和其他活动设计器拖到**流程图**、<xref:System.Activities.Activity>它们表示的对象就可以链接在一起若要指定执行顺序。 创建一个<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>与关联<xref:System.Activities.Statements.FlowSwitch%601>，单击其中一个的外围网络上的正方形 case 处理**FlowSwitch < T\>** 并将其拖到其中一个的句柄的 （通过按住鼠标按钮）当鼠标悬停在其设计器时出现在目标活动周围类似的方式。 松开鼠标按钮和从一个箭头**FlowSwitch < T\>** 到目标设计器中显示表示这种情况。 默认值为这种情况下显示的箭头，并可以在中进行编辑**用例**框**属性**窗口。  
  
### <a name="the-flowswitcht-properties"></a>FlowSwitch < T\>属性  
 下表列出 <xref:System.Activities.Statements.FlowSwitch%601> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|指定表达式，通过计算该表达式来确定在执行路径中可切换到哪个 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|指定通过从 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 的可能计算结果到一组 <xref:System.Activities.Statements.FlowNode> 对象的唯一映射。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|指定当 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 的计算值与 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 对象中包含的值之一不匹配时的映射。|  
  
## <a name="see-also"></a>另请参阅  
 [流程图](../workflow-designer/flowchart-activity-designers.md)   
 [流程图](../workflow-designer/flowchart-activity-designer.md)   
 [Flowdecision](../workflow-designer/flowdecision-activity-designer.md)