---
title: "Persist 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0fa7868d814b1ee5079cba69b9d54665ad1e4a47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="persist-activity-designer"></a>Persist 活动设计器
**保留**活动设计器用于创建和配置<xref:System.Activities.Statements.Persist>活动。  
  
## <a name="the-persist-activity"></a>Persist 活动  
 <xref:System.Activities.Statements.Persist> 活动用于将工作流保存到磁盘中（如有可能）。 <xref:System.Activities.Statements.Persist> 活动无法在非持久性区域中执行，例如，在 <xref:System.Activities.Statements.TransactionScope> 活动中。 如果在非持久性作用域中使用 <xref:System.Activities.Statements.Persist> 活动，则在运行时会引发异常。  
  
### <a name="using-the-persist-activity-designer"></a>使用 Persist 活动设计器  
 **保留**在找不到活动设计器**运行时**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡 (或者，选择**工具箱**从**视图**菜单或 CTRL + ALT + X。)  
  
 **保留**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建<xref:System.Activities.Statements.Persist>默认值的活动**DisplayName**的保留。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**保留**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-persist-properties"></a>Persist 属性  
 下表列出 <xref:System.Activities.Statements.Persist> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 活动的友好名称。 默认值为 Persist。 虽然显示名称不是绝对必需的，但最好使用显示名称。|  
  
## <a name="see-also"></a>另请参阅  
 [运行时](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)