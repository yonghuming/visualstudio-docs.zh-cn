---
title: "Switch&lt;T&gt; 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.ModelItemKeyValuePair.UI"
  - "System.Activities.Statements.Switch`1.UI"
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
caps.handback.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Switch&lt;T&gt; 活动设计器
<xref:System.Activities.Statements.Switch%601> 活动计算指定表达式并执行活动集合中其关联键与计算所得值匹配的活动。  
  
 **“Switch\<T\>”**活动设计器用于在 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中创建和配置 <xref:System.Activities.Statements.Switch%601> 活动。  
  
## Switch\<T\> 活动  
 一个 <xref:System.Activities.Statements.Switch%601> 活动包含一个 <xref:System.Activities.Statements.Switch%601.Expression%2A> 和一个 <xref:System.Activities.Statements.Switch%601.Cases%2A> 的字典。该字典中的每个 case 都包含由一个 *key* 和一个用作其对应 *value* 的活动组成的对。<xref:System.Activities.Statements.Switch%601> 活动计算 <xref:System.Activities.Statements.Switch%601.Expression%2A> 并将其与每个键相比较。如果找到匹配项，则会执行对应的活动。只可能有一个匹配项，因为字典键与字典的相等比较器所定义的相等类型的对应必须是唯一的。如果未找到匹配项，则会执行 <xref:System.Activities.Statements.Switch%601.Default%2A> 活动。  
  
## 如何使用 Switch\<T\> 活动设计器  
 **“Switch\<T\>”**活动设计器可在**“工具箱”**的**“控制流”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。将该活动设计器放入 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中后，它将显示**“选择类型”**对话框，用户可在其中指定 <xref:System.Activities.Statements.Switch%601> 活动中使用的泛型类型 *T*。默认值为 **Int32**。选择泛型类型 *T* 后，**“Switch\<T\>”**设计器将添加到工作流设计器中。  
  
 下面是**“Switch\<T\>”**设计器的属性。所有这些属性都可以在属性网格中进行编辑。其中一些属性还可以在设计器图面上进行编辑。  
  
 下表列出最有用的 <xref:System.Activities.Statements.Switch%601> 属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Switch%601> 活动设计器的友好名称。默认值为 Switch\<Int32\>。可以在**“属性”**窗口或直接在设计器标头中编辑该值。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|指定用于与 case 集合中的键进行比较以确定执行哪个 case 的表达式。|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||指定未找到匹配项时执行的活动。单击设计器上的**“添加活动”**按钮将打开**“默认值”**框，可在其中放入该活动。|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||指定要计算的 case。若要添加 case，请单击**“Switch\<T\>”**设计器底部的**“添加新事例”**按钮。按钮将变为文本框（如果在添加 Switch\<T\> 时选择的泛型类型为 String 或 Enum，则变为组合框）。在**“Case 值”**框中添加键后，case 区域将展开，可在提示文本“在此处放置活动”处放置活动以定义该 case 的执行逻辑。|  
  
 可以添加多个 case，但 case 键不能重复。否则将显示一个错误对话框，报告指定 case 键已存在，您必须选择其他键。在**“Switch\<T\>”**设计器中，一次只有一个 case 区域能以展开的视图显示。某个 case 区域为折叠的视图时，单击该 case 区域即可展开它。请注意，对于折叠的 case，如果该活动有显示名称，设计器将在该 case 内的右侧显示该显示名称。否则将显示**“添加活动”**按钮，单击该按钮将展开 case，可以在其中添加活动。  
  
 单击现有 case 的键可将该键从标签变为文本框，从而可以编辑该 case 键。  
  
 删除 case 的方法有两种：  
  
1.  选中相应 case，然后删除它。  
  
2.  选中相应 case，右击以显示上下文菜单，然后选择**“删除”**。  
  
 请注意，必须选中 case 本身才能删除它。选中并删除 case 内的活动只会删除该活动而不会删除该 case。  
  
## 请参阅  
 [控制流](../workflow-designer/control-flow-activity-designers.md)