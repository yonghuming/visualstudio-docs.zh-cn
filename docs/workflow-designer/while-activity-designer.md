---
title: "While 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: b70e0c66813c474d5711538843da93a669df88d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="while-activity-designer"></a>While 活动设计器
<xref:System.Activities.Statements.While>活动执行中包含的活动其<xref:System.Activities.Statements.While.Body%2A>时指定<xref:System.Activities.Statements.While.Condition%2A>计算结果为**true**。 包含的活动可能永远都不会执行。 如果希望所包含的活动至少执行一次，请改用 <xref:System.Activities.Statements.DoWhile> 活动。  
  
## <a name="while-properties-in-workflow-designer"></a>工作流设计器中的 While 属性  
 下表列出最有用的 <xref:System.Activities.Statements.While> 活动属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.While> 活动设计器在标头中的友好名称。 默认值为 While。 可以在中编辑值**属性**窗口或直接在活动设计器标头。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.While.Body%2A>|False|包含要执行的活动时<xref:System.Activities.Statements.While.Condition%2A>计算结果为**true**。|  
|<xref:System.Activities.Statements.While.Condition%2A>|True|包含 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 表达式，通过计算该表达式来确定是否要执行 <xref:System.Activities.Statements.While.Body%2A> 中的活动。|  
  
## <a name="see-also"></a>另请参阅  
 [控制流](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)