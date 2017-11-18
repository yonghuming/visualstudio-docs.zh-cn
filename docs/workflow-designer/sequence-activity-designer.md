---
title: "序列活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51f138d17c2b0f8d8a483ef09c298d1dbbf9345c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="sequence-activity-designer"></a>Sequence 活动设计器
<xref:System.Activities.Statements.Sequence> 活动包含子活动的已排序集合，将按该排序执行这些子活动。  
  
 按顺序执行一组活动的另一个方法是使用 <xref:System.Activities.Statements.Flowchart> 活动。 请考虑使用[流程图](../workflow-designer/flowchart-activity-designer.md)当具有简单分支或循环你想要 diagrammatically 模型的程序流。  
  
## <a name="using-the-sequence-activity-designer"></a>使用 Sequence 活动设计器  
 若要添加<xref:System.Activities.Statements.Sequence>活动，请将**序列**活动设计器从**工具箱**拖放到[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]面。 若要将子活动添加到此<xref:System.Activities.Statements.Sequence>活动，将一些其他活动从**工具箱**并将其放在带提示文本框中的三角形上"此处放置活动"。  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>工作流设计器中的 Sequence 活动属性  
 下表列出 <xref:System.Activities.Statements.Sequence> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Sequence> 活动设计器在标头中的友好名称。 默认值为 Sequence。 可以在属性网格或直接在活动设计器的标头中编辑该值。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
  
## <a name="see-also"></a>另请参阅  
 [流程图](../workflow-designer/flowchart-activity-designer.md)   
 [控制流](../workflow-designer/control-flow-activity-designers.md)