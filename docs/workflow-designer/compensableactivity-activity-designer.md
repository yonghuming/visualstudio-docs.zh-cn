---
title: "CompensableActivity 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7523327fe63bfd00fb5bc5ce4f98aeef61a2567
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 活动设计器
**CompensableActivity**活动设计器用于创建和配置<xref:System.Activities.Statements.CompensableActivity>活动。  
  
## <a name="the-compensableactivity-activity"></a>CompensableActivity 活动  
 <xref:System.Activities.Statements.CompensableActivity> 定义可在成功完成之后得到确认或补偿的工作单元。  
  
### <a name="using-the-compensableactivity-activity-designer"></a>使用 CompensableActivity 活动设计器  
 **CompensableActivity**在找不到活动设计器**事务**类别**工具箱**，通过单击访问的哪一**工具箱**的左侧选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **CompensableActivity**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建具有 CompensableActivity 的默认 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑值**CompensableActivity**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-compensableactivity-properties"></a>CompensableActivity 属性  
 下表列出 <xref:System.Activities.Statements.CompensableActivity> 属性并说明如何在设计器中使用它们。 <xref:System.Activities.Activity.DisplayName%2A> 和 <xref:System.Activities.Activity%601.Result%2A> 属性可在属性网格中进行编辑，但其他属性必须在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> 活动的可选友好名称。 默认值为 CompensableActivity。|  
|<xref:System.Activities.Activity%601.Result%2A>|False|指定 <xref:System.Activities.Statements.CompensableActivity> 的返回值。 此属性必须在属性网格中进行编辑。|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|指定为其提供补偿、取消和确认逻辑的活动。 若要添加<xref:System.Activities.Statements.CompensableActivity.Body%2A>活动，将活动从**工具箱**到**正文**框**CompensableActivity**带提示文本"放置活动设计器在此处活动"。|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|指定在取消事件中执行的活动。 若要添加活动，删除其设计器从**工具箱**到**拖放**框**CompensableActivity**带提示文本"放置活动设计器在此处活动"。|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|指定补偿 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活动时要执行的活动。 可使用 <xref:System.Activities.Statements.Compensate> 活动显式调用此处理程序。<br /><br /> 若要添加活动，删除其活动设计器从**工具箱**到**CompensationHandler**框**CompensableActivity**带提示文本的活动设计器"在此处放置活动"。|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|指定确认 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活动时要执行的活动。 可使用 <xref:System.Activities.Statements.Confirm> 活动显式调用此处理程序。<br /><br /> 若要添加活动，删除其活动设计器从**工具箱**到**ConfirmationHandler**框**CompensableActivity**带提示文本的活动设计器"在此处放置活动"。|  
  
## <a name="see-also"></a>另请参阅  
 [事务](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [补偿](../workflow-designer/compensate-activity-designer.md)   
 [确认](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)