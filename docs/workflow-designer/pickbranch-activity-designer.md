---
title: "PickBranch 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a77adbe5e2663ef11242d162b6ac718d88daea5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="pickbranch-activity-designer"></a>PickBranch 活动设计器
<xref:System.Activities.Statements.PickBranch> 在可由传入事件触发的 <xref:System.Activities.Statements.Pick> 活动中提供基于事件的执行路径。  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch> 对象包含在 <xref:System.Activities.Statements.Pick.Branches%2A> 活动的 <xref:System.Activities.Statements.Pick> 集合中。 每个 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活动的一个分支中，并可因某些用作触发器的传入事件而执行。 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 由此提供基于事件的控制流建模。 每个 <xref:System.Activities.Statements.PickBranch> 都包含一个 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 和一个 <xref:System.Activities.Statements.PickBranch.Action%2A>。  
  
### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活动设计器  
 **Pickbranch**在找不到设计器**控制流**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X)。  
  
 两个空<xref:System.Activities.Statements.PickBranch>对象显示名称为**Branch1**和**Branch2**默认情况下创建的元素作为<xref:System.Activities.Statements.Pick>活动时**选取**最初，活动设计器放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。 二者各自<xref:System.Activities.Statements.PickBranch.DisplayName%2A>属性值可以在中编辑**pickbranch**设计器标头或**属性**为每个分支的窗口。  
  
 有两种方法来添加<xref:System.Activities.Statements.PickBranch>到的集合对象<xref:System.Activities.Statements.Pick>对象： 中拖放**pickbranch**从设计器**工具箱**或通过从上下文菜单在**选取**设计图面：  
  
1.  **Pickbranch**设计器将创建<xref:System.Activities.Statements.PickBranch>时从拖**工具箱**，放入的分支中的一个**选取**上的活动设计器[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]面。 新 <xref:System.Activities.Statements.PickBranch> 对象可放置在 <xref:System.Activities.Statements.Pick> 设计器内已包含在集合中的任何现有 <xref:System.Activities.Statements.PickBranch> 元素的左侧或右侧。 拖动时**pickbranch**设计器拖到**选取**使用鼠标，设计器**选取**设计器使用垂直的蓝灰条来指示在何处<xref:System.Activities.Statements.PickBranch>为给定的鼠标放置位置添加了。  
  
2.  右键单击**选取**活动设计器 (但不是能在**pickbranch**设计器) 获取上下文菜单并选择**创建分支**添加新<xref:System.Activities.Statements.PickBranch>。 请注意，新<xref:System.Activities.Statements.PickBranch>添加到现有的右侧<xref:System.Activities.Statements.PickBranch>中的对象**选取**设计器。  
  
 **Pickbranch**设计器可以展开以显示**触发器**和**操作**框或通过单击其标头右侧的双插入符号折叠。 编辑<xref:System.Activities.Statements.PickBranch.Trigger%2A>和<xref:System.Activities.Statements.PickBranch.Action%2A>每个<xref:System.Activities.Statements.PickBranch>通过将活动放入**触发器**和**操作**相应设计器的框。  
  
 <xref:System.Activities.Statements.PickBranch>中的对象<xref:System.Activities.Statements.Pick.Branches%2A>集合<xref:System.Activities.Statements.Pick>对象，可以通过拖放至中的新位置重新排序**选取**设计器。 **选取**设计器使用垂直的蓝灰条来指示在何处<xref:System.Activities.Statements.PickBranch>添加对给定的鼠标放置位置。  
  
 有两种方法可删除 <xref:System.Activities.Statements.PickBranch>：  
  
1.  选择**pickbranch**设计器并将其删除。  
  
2.  选择**pickbranch**设计器中，右键单击以获取上下文菜单并选择**删除**。  
  
 请务必选择**pickbranch**设计器中，选择其中一个内的活动作为其**触发器**或**操作**框是误删除这些活动之一而不<xref:System.Activities.Statements.PickBranch>对象。  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>工作流设计器中的 PickBranch 属性  
 下表列出最有用的 <xref:System.Activities.Statements.PickBranch> 属性并说明如何在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中使用它们。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|标题上显示的友好名称**pickbranch**设计器。 默认值为 Branch。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|每个 <xref:System.Activities.Statements.PickBranch> 都包含一个可调用 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 的 <xref:System.Activities.Statements.PickBranch.Action%2A> 操作。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|每个 <xref:System.Activities.Statements.PickBranch> 都包含一个触发时将执行的 <xref:System.Activities.Statements.PickBranch.Action%2A>。|  
  
## <a name="see-also"></a>另请参阅  
 [控制流](../workflow-designer/control-flow-activity-designers.md)   
 [Pick 活动](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [使用 Pick 活动](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)