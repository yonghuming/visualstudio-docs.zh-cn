---
title: "Pick 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: "9"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa06d4c63dbb18c080c8a6b8ffda01838607ba55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="pick-activity-designer"></a>Pick 活动设计器
<xref:System.Activities.Statements.Pick> 活动提供基于事件的控制流。 该活动执行多个分支中的一个分支来响应某个触发的事件。  
  
## <a name="the-pick-activity"></a>Pick 活动  
 <xref:System.Activities.Statements.Pick> 活动包含一个 <xref:System.Activities.Statements.PickBranch> 对象的集合，<xref:System.Activities.Statements.Pick> 活动会由于某些作为触发器的传入事件而执行其中一个对象。 因此，[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供了基于事件的控制流建模。 每个 <xref:System.Activities.Statements.PickBranch> 都包含一个 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 和一个 <xref:System.Activities.Statements.PickBranch.Action%2A>。 开头的<xref:System.Activities.Statements.Pick>活动的执行的所有触发器活动<xref:System.Activities.Statements.PickBranch>计划元素。 在第一个活动完成之后，安排其相应的操作活动，并且取消所有其他触发器活动。  
  
### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活动设计器  
 **选取**在找不到活动设计器**控制流**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单或 CTRL + ALT + X。)  
  
 **选取**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面活动设计器放置的任何位置通常情况下，例如内**序列**活动设计器。 将该设计器放置到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中之后，它会创建一个 <xref:System.Activities.Statements.Pick> 活动，默认情况下，该活动包含两个空的 <xref:System.Activities.Statements.PickBranch> 活动，作为显示名称为 Branch1 和 Branch2 的元素。 二者各自<xref:System.Activities.Statements.PickBranch.DisplayName%2A>属性值可以在中编辑**pickbranch**活动设计器标头或**属性**为每个分支的窗口。  
  
 有两种方法来添加<xref:System.Activities.Statements.PickBranch>到的集合的活动<xref:System.Activities.Statements.Pick>对象： 中拖放**pickbranch**从设计器**工具箱**或通过从上下文菜单在**选取**设计图面。 有关详细信息，请参阅[pickbranch](../workflow-designer/pickbranch-activity-designer.md)主题。 请注意，唯一项可以放置在**选取**活动设计器是**pickbranch**活动设计器。  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>工作流设计器中的 Pick 活动属性  
 下表列出 <xref:System.Activities.Statements.Pick> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Pick> 活动设计器在标头中的友好名称。 默认值为 Pick。 可以在属性网格或直接在活动设计器的标头中编辑该值。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
  
## <a name="see-also"></a>另请参阅  
 [控制流](../workflow-designer/control-flow-activity-designers.md)   
 [Pick 活动](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [使用 Pick 活动](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)