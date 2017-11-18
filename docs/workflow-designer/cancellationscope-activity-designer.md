---
title: "CancellationScope 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b2ad28e6b89273b5fdb55e4cfa35d1df292221a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 活动设计器
**CancellationScope**活动设计器用于创建和配置<xref:System.Activities.Statements.CancellationScope>活动。  
  
## <a name="the-cancellationscope-activity"></a>CancellationScope 活动  
 使用 <xref:System.Activities.Statements.CancellationScope> 活动可指定要执行的活动以及该活动的取消逻辑。  
  
### <a name="using-the-cancellationscope-activity-designer"></a>使用 CancellationScope 活动设计器  
 **CancellationScope**在找不到活动设计器**事务**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **CancellationScope**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建具有 CancellationScope 的默认 <xref:System.Activities.Statements.CancellationScope> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑值**CancellationScope**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-cancellationscope-properties"></a>CancellationScope 属性  
 下表列出 <xref:System.Activities.Statements.CancellationScope> 属性并说明如何在设计器中使用它们。 <xref:System.Activities.Activity.DisplayName%2A> 属性可在属性网格中编辑，但其他属性必须在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 活动的可选友好名称。 默认值为 CancellationScope。 虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|指定为其提供取消逻辑的活动。 若要添加<xref:System.Activities.Statements.CancellationScope.Body%2A>活动，将活动从**工具箱**到**正文**框**CancellationScope**带提示文本"放置活动设计器在此处活动"。|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|指定在取消事件中执行的活动。 若要添加<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>活动，将活动从**工具箱**到**拖放**框**CancellationScope**附带提示的活动设计器文本"此处放置活动"。|  
  
## <a name="see-also"></a>另请参阅  
 [事务](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [补偿](../workflow-designer/compensate-activity-designer.md)   
 [确认](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)