---
title: "TryCatch 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TryCatch 活动设计器
**“TryCatch”**活动设计器用于创建和配置 <xref:System.Activities.Statements.TryCatch> 活动。  
  
## TryCatch 活动  
 <xref:System.Activities.Statements.TryCatch> 活动包含一个 <xref:System.Activities.Statements.TryCatch.Try%2A> 活动、一个 **Catch\<TException\>** 集合和一个 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活动。一个类型为 **TException** 的 <xref:System.Activities.Statements.Catch%601> 包含一个 <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> 和一个 <xref:System.Activities.Statements.Catch%601.Action%2A>。将它们结合使用可实现典型的基于异常的错误处理机制。<xref:System.Activities.Statements.TryCatch> 活动尝试执行其 <xref:System.Activities.Statements.TryCatch.Try%2A> 活动。如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 活动引发任何异常，则 <xref:System.Activities.Statements.TryCatch> 活动会使用其 **Catch\<TException\>** 集合来匹配该异常。如果存在匹配，则执行相应 **Catch\<TException\>** 的 <xref:System.Activities.Statements.Catch%601.Action%2A>，作为该异常的错误处理逻辑。如果在活动 <xref:System.Activities.Statements.TryCatch.Try%2A> 节成功完成或在活动 <xref:System.Activities.Statements.TryCatch.Catches%2A> 已成功完成，<xref:System.Activities.Statements.TryCatch> 活动执行其 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活动。[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][异常](../Topic/Exceptions.md).  
  
### 使用 TryCatch 活动设计器  
 **“TryCatch”**活动设计器可在**“工具箱”**的**“错误处理”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左侧的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“TryCatch”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 TryCatch 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.Activities.Statements.TryCatch> 活动。可以在**“TryCatch”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A> 值。其他属性必须在**“TryCatch”**活动设计器的图面上编辑。  
  
 单击**“TryCatch”**设计器右上角的展开按钮，可以在展开的视图中看到**“Try”**、**“Catches”**和**“Finally”**框。若要添加 catch，请单击**“TryCatch”**设计器上的**“添加新捕获”**按钮。该按钮将变为类型组合框。选择一个异常类型，然后按 Enter 键添加该 catch。添加 **Catch** 后，catch 区域将展开，可以在 catch 中放入活动以定义该 catch 的执行逻辑。请注意，在展开的 catch 区域右侧有一个文本框。可以使用此文本框为异常变量命名。异常变量只能用于同一 **Catch** 中的活动。  
  
 **“TryCatch”**设计器不支持编辑 **Catch**。若要更改异常类型，必须先删除现有 **Catch**，再添加一个新的。删除 **Catch** 的一种方法是选中它然后删除，另一种方法是通过右击使用上下文菜单中的**“删除”**菜单。  
  
### TryCatch 属性  
 下表列出 <xref:System.Activities.Statements.TryCatch> 属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.TryCatch> 活动的可选友好名称。默认方法 TryCatch。|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|在 <xref:System.Activities.Statements.TryCatch> 执行时首先执行的活动。|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|<xref:System.Activities.Statements.TryCatch.Try%2A> 活动引发异常时要检查的 **Catch** 元素的集合。<br /><br /> 需要在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 中至少添加一个活动或在 <xref:System.Activities.Statements.TryCatch.Finally%2A> 块中添加一个活动。|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|执行完 <xref:System.Activities.Statements.TryCatch.Try%2A> 以及 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合中的任何必要活动时要执行的活动。<br /><br /> 需要在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 中至少添加一个活动或在 <xref:System.Activities.Statements.TryCatch.Finally%2A> 块中添加一个活动。|  
  
## 请参阅  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)