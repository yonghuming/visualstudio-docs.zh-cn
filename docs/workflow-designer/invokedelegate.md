---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# InvokeDelegate
**“InvokeDelegate”**设计器用于创建和配置 <xref:System.Activities.Statements.InvokeDelegate> 活动。  
  
## InvokeDelegate 活动  
 <xref:System.Activities.Statements.InvokeDelegate> 调用公众委托。  
  
### 使用 InvokeDelegate 活动设计器  
 **“InvokeDelegate”**活动设计器可在**“工具箱”**的**“基元”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“InvokeDelegate”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 InvokeDelegate 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.Activities.Statements.InvokeDelegate> 活动。可以在**“InvokeDelegate”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
### InvokeDelegate 属性  
 下表列出 <xref:System.Activities.Statements.InvokeDelegate> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 活动的友好名称。 默认值为 InvokeDelegate。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|要在执行活动时调用的 <xref:System.Activities.Statements.ActivityDelegate> 的名称。此属性可以在设计器图面上进行编辑。此属性是强制属性。|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|调用委托的参数集合。键为 <xref:System.Activities.Statements.ActivityDelegate> 上的 <xref:System.Activities.Statements.ActivityDelegateParameter> 对象的名称，值为其表达式将进行计算并分配给对应 <xref:System.Activities.Statements.ActivityDelegateParameter> 对象的参数。在属性网格中，单击**“DelegateArguments”**字段中的省略号按钮，此时将显示**“DelegateArguments”**对话框以便您设置此属性。单击**“创建参数”** 字段以添加参数。|  
  
## 请参阅  
 [如何：在工作流设计器中定义和使用活动委托](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)