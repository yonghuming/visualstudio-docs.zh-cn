---
title: "AddToCollection&lt;T&gt; 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.AddToCollection`1.UI"
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# AddToCollection&lt;T&gt; 活动设计器
**“AddToCollection\<T\>”**活动设计器用于创建和配置 <xref:System.Activities.Statements.AddToCollection%601> 活动。  
  
## AddToCollection\<T\> 活动  
 <xref:System.Activities.Statements.AddToCollection%601> 活动向集合添加一项。  
  
### 使用 AddToCollection\<T\> 活动设计器  
 **“AddToCollection\<T\>”**活动设计器可在**“工具箱”**的**“集合”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“AddToCollection\<T\>”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 AddToCollection\<Int32\> 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.Activities.Statements.AddToCollection%601> 活动。（默认情况下，*TypeArgument* 为 **Int32**。可在属性网格中更改此值。）可以在**“AddToCollection\<T\>”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A> 值。其他属性必须在属性网格上编辑。  
  
### AddToCollection\<T\> 属性  
 下表列出 <xref:System.Activities.Statements.AddToCollection%601> 属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 活动的友好名称。默认值为 AddToCollection\<Int32\>。虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|要添加到 Collection\<T\> 中的项。此项的类型 *T* 为 *TypeArgument* 类型。若要指定项，请在属性网格中键入 Visual Basic 表达式。|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|项应添加到的集合。此集合的类型为 **ICollection\<TypeArgument\>**。若要指定集合，请在属性网格中键入 Visual Basic 表达式。|  
|*TypeArgument*|True|包含在 <xref:System.Collections.Generic.ICollection%601> 中的项的类型 T。默认情况下，此 *TypeArgument* 类型设置为 **Int32**。若要更改类型，请在属性网格的组合框中更改 *TypeArgument* 的值。|  
  
## 请参阅  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\> Activity Designer](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)