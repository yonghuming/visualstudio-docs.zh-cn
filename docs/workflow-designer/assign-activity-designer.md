---
title: "Assign 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 87398c82d0a22c79d852292fef3f86abe63a443d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="assign-activity-designer"></a>Assign 活动设计器
**分配**活动设计器用于创建和配置<xref:System.Activities.Statements.Assign>活动。  
  
## <a name="the-assign-activity"></a>Assign 活动  
 <xref:System.Activities.Statements.Assign> 活动为变量或参数赋值。  
  
### <a name="using-the-assign-activity-designer"></a>使用 Assign 活动设计器  
 **分配**在找不到活动设计器**基元**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡 (或者，选择**工具箱**从**视图**菜单或 CTRL + ALT + X。)  
  
 **分配**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建<xref:System.Activities.Statements.Assign>默认值的活动**DisplayName**的分配。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**分配**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-assign-properties"></a>Assign 属性  
 下表列出 <xref:System.Activities.Statements.Assign> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> 活动的友好名称。 默认值为 Assign。 虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|为其赋 <xref:System.Activities.Statements.Assign.Value%2A> 的变量或参数。 它必须是有效的 Visual Basic 标识符。 若要设置该属性，键入在 Visual Basic 表达式**到**框**分配**活动设计器或在属性网格中。|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|赋给变量的值。 若要设置<xref:System.Activities.Statements.Assign.Value%2A>，键入在 Visual Basic 表达式**值**框**分配**活动设计器或在属性网格中。|  
  
## <a name="see-also"></a>另请参阅  
 [基元](../workflow-designer/primitives-activity-designers.md)   
 [延迟](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)