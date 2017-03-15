---
title: "WriteLine 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# WriteLine 活动设计器
**“WriteLine”**活动设计器用于创建和配置 <xref:System.Activities.Statements.WriteLine> 活动。  
  
## WriteLine 活动  
 <xref:System.Activities.Statements.Writeline> 活动将文本写入指定的 <xref:System.IO.TextWriter> 对象。如果未指定 <xref:System.IO.TextWriter>，则 <xref:System.Activities.Statements.Writeline> 会将文本写入控制台中。  
  
### 使用 WriteLine 活动设计器  
 **“WriteLine”**活动设计器可在**“工具箱”**的**“基元”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“WriteLine”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 WriteLine 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.Activities.Statements.WriteLine> 活动。可以在**“WriteLine”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
### WriteLine 属性  
 下表列出 <xref:System.Activities.Statements.WriteLine> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.WriteLine> 活动的友好名称。默认值为 WriteLine。虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|要写入的文本。若要设置该属性，请在**“WriteLine”**活动设计器或属性网格中的**“文本”**框中键入 Visual Basic 表达式。|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.Activities.Statements.WriteLine> 向其写入 <xref:System.Activities.Statements.WriteLine.Text%2A> 的 <xref:System.IO.TextWriter>。默认为控制台。|  
  
## 请参阅  
 [基元](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)