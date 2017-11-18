---
title: "TerminateWorkflow 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a3b7c7cf56aa465f88ae918056e2d71ad6c41e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow 活动设计器
**TerminateWorkflow**活动设计器用于创建和配置<xref:System.Activities.Statements.TerminateWorkflow>活动。  
  
## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow 活动  
 <xref:System.Activities.Statements.TerminateWorkflow> 活动终止工作流的执行。  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>使用 TerminateWorkflow 活动设计器  
 **TerminateWorkflow**在找不到活动设计器**运行时**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡 (或者，选择**工具箱**从**视图**菜单或 CTRL + ALT + X。)  
  
 **TerminateWorkflow**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建<xref:System.Activities.Statements.TerminateWorkflow>默认值的活动**DisplayName** TerminateWorkflow。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**TerminateWorkflow**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow 属性  
 下表列出 <xref:System.Activities.Statements.TerminateWorkflow> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> 活动的友好名称。 默认值为 TerminateWorkflow。 虽然显示名称不是绝对必需的，但最好使用显示名称。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|终止工作流时要引发的异常。 此属性在属性网格中设置。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|解释终止工作流的原因。 此属性在属性网格中设置。|  
  
## <a name="see-also"></a>另请参阅  
 [运行时](../workflow-designer/runtime-activity-designers.md)   
 [保留](../workflow-designer/persist-activity-designer.md)