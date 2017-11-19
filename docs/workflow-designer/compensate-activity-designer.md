---
title: "Compensate 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7fa3d16f87f6c81f0f9a4abfb961754ce7882f4c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="compensate-activity-designer"></a>Compensate 活动设计器
**Compensate**活动设计器用于创建和配置<xref:System.Activities.Statements.Compensate>活动。  
  
## <a name="the-compensate-activity"></a>Compensate 活动  
 <xref:System.Activities.Statements.Compensate> 活动为 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 中包含的活动显式调用 <xref:System.Activities.Statements.CompensableActivity>。 如果 <xref:System.Activities.Statements.Compensate> 活动未在 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 的 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity> 中使用，则必须指定 <xref:System.Activities.Statements.Compensate.Target%2A> 属性。  
  
 由 <xref:System.Activities.Statements.CompensationToken> 指定的 <xref:System.Activities.Statements.Compensate.Target%2A> 提供了在 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 成功完成之后显式确认或补偿 <xref:System.Activities.Statements.CompensableActivity> 的方法。  
  
### <a name="using-the-compensate-activity-designer"></a>使用 Compensate 活动设计器  
 **Compensate**在找不到活动设计器**事务**类别**工具箱**，通过单击访问的哪一**工具箱**的左侧选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **Compensate**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建具有 Compensate 的默认 <xref:System.Activities.Statements.Compensate> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑值**Compensate**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-compensate-properties"></a>Compensate 属性  
 下表列出 <xref:System.Activities.Statements.CancellationScope> 属性并说明如何在设计器中使用它们。 <xref:System.Activities.Activity.DisplayName%2A> 属性可在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑，但 <xref:System.Activities.Statements.Compensate.Target%2A> 属性必须在属性网格中编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Compensate> 活动的可选友好名称。 默认值为 Compensate。|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|指定 <xref:System.Activities.InArgument%601>，它包含此 <xref:System.Activities.Statements.CompensationToken> 活动的 <xref:System.Activities.Statements.Compensate>。|  
  
## <a name="see-also"></a>另请参阅  
 [事务](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate 活动设计器](../workflow-designer/compensate-activity-designer.md)   
 [确认](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)