---
title: "事务活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Transition.UI"
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "sdanie"
manager: "erikre"
---
# 事务活动设计器
<xref:System.Activities.Statements.Transition> 表示两个状态间的转换。  
  
## 使用转换活动设计器  
 转换活动设计器允许您在两个状态之间配置转换。  
  
### 工作流设计器中的转换属性  
 下表列出可使用工作流设计器的 <xref:System.Activities.Statements.Transition> 活动属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Transition> 活动设计器的友好名称。默认值为 **T1**。可在属性栅格、扩展的转换设计器的标头以及扩展转换设计器的操作部分的标头中，编辑值。<xref:System.Activities.Activity.DisplayName%2A> 中的工作流设计器顶部显示的痕迹导航中使用。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|如果存在，则必须在控件传递给目标状态前评估为 **True** 的表达式。可以在属性栅格和扩展的转化设计器中编辑条件。在共享转化中的多个条件按显示在转换设计器中的顺序进行评估。 **Note:**  注意，如果转换的 <xref:System.Activities.Statements.Transition.Condition%2A> 计算结果为 **False** （或所有的共享触发转换的计算结果为 **False**\)，转换将不发生并且此状态下的所有转换的所有触发将被重新计划。在本教程中，由于配置条件的方式这种情况不会发生（我们有猜测是否是正确的或不正确的具体行动）。|  
|**源**|True|指示源自此转换的状态。单击源状态的名称将视图设计器视图转换为状态的扩展视图。在创建转换时设置此值，并且不能更改该值。|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|指定其完成启动转换的活动。若要设置此活动，将活动从**“工具箱”**拖动，并将其拖至转换的**“触发器”**部分。|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|指定活动完成时执行的活动和 <xref:System.Activities.Statements.Transition.Condition%2A>，如果存在，则评估为 **true**。在源状态的<xref:System.Activities.Statements.State.Exit%2A> 活动后，转换到目标状态时执行此活动，如果存在，则执行。当扩展转换设计器，此值可以是通过从**“工具箱”**中拖动活动并拖至该转换的**“操作”**部分。可以有单一转换的多个操作。可以展开和收缩个别的操作，在转换中存在多个操作时可通过单击在操作上时显示的向上或向下箭头键进行排序。|  
|**目标**|True|指示转换完成后状态计算机转换到的状态。这与对象模型中的转换的 <xref:System.Activities.Statements.Transition.To%2A> 属性相对应。单击目标状态的名称将视图设计器视图转换为状态的扩展视图。在创建转化时设置此值，并可以通过拖动将转换连接到设计器中的目标属性的箭头进行更改。|  
  
### 创建转换  
 通过将某行从一个状态拖到另一个状态，或在从一个状态拖动到另一个状态时通过将状态拖放到出现的三角形上，来创建转换。若要通过拖动来创建转换，则将鼠标悬停源状态的边缘，并将某行从源状态拖到目标状态。若要通过拖放方式创建转换，将其悬停在源状态，并将它拖到源状态周围显示的四个矩形之一。目标状态从**“工具箱”**拖动的新状态可以为新状态，也可以为从工作流设计器中拖动的现有状态。  
  
> [!NOTE]
>  状态机中的单个状态使用工作流设计器可以创建多达 76 种转换。对在设计器外创建的工作流中的状态转换的限制只受系统资源限制。  
  
 共享触发器转换是共享相同的触发事件的一组转换。条件进展的共享触发器允许目标状态（基于共享常用触发器时间的多个转换配置的表达式评估）。若要将其他操作添加到转换和创建共享转换，请单击圆圈，以指示所需转换的开始，并将它拖动到所需的状态。新转换将以初始转换的形式共享同一触发器，但它将具有一个唯一的条件和操作。也可以通过单击转换设计器底部的**“添加共享的触发器转换”**，再选择**“连接的可用状态”**下列表中的所需目标状态，在转换设计器中创建共享转换。  
  
## 请参阅  
 [状态机](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [状态](../workflow-designer/state-activity-designer.md)