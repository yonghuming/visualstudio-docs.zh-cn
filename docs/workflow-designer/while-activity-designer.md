---
title: "While 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# While 活动设计器
当指定的 <xref:System.Activities.Statements.Condition%2A> 的计算结果为 **true** 时，<xref:System.Activities.Statements.While> 活动执行其 <xref:System.Activities.Statements.While.Body%2A> 中包含的活动。包含的活动可能永远都不会执行。如果希望所包含的活动至少执行一次，请改用 <xref:System.Activities.Statements.DoWhile> 活动。  
  
## 工作流设计器中的 While 属性  
 下表列出最有用的 <xref:System.Activities.Statements.While> 活动属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.While> 活动设计器在标头中的友好名称。默认值为 While。可以在**“属性”**窗口或直接在活动设计器标头中编辑该值。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.While.Body%2A>|False|包含当 <xref:System.Activities.Statements.Condition%2A> 的计算结果为 **true** 时要执行的活动。|  
|<xref:System.Activities.Statements.Condition%2A>|True|包含 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 表达式，通过计算该表达式来确定是否要执行 <xref:System.Activities.Statements.While.Body%2A> 中的活动。|  
  
## 请参阅  
 [控制流](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)