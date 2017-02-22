---
title: "ParallelForEach&lt;T&gt; 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ParallelForEach&lt;T&gt; 活动设计器
<xref:System.Activities.Statements.ParallelForEach%601> 活动枚举集合元素并对集合中的每个元素并行执行嵌入语句，这将在同一线程上异步执行。如果此活动的子活动预期会进入空闲状态，请使用此流控制活动，而不是 <xref:System.Activities.Statements.Sequence> 活动。  
  
 <xref:System.Activities.Statements.ParallelForEach%601> 活动有一个 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 属性，该属性包含用户指定的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 表达式。<xref:System.Activities.Statements.ParallelForEach%601> 活动在完成每个分支后计算此属性。如果计算结果为 **true**，则 <xref:System.Activities.Statements.ParallelForEach%601> 活动完成，无需执行其他分支。如果 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 计算结果不为 **true**，则 <xref:System.Activities.Statements.ParallelForEach%601> 活动在完成其所有子活动后完成。  
  
## ParallelForEach\<T\> 活动  
 <xref:System.Activities.Statements.ParallelForEach%601> 枚举其值并为枚举的每个值安排 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 的执行顺序。仅安排 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 的执行顺序。Body 的执行方式取决于 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 是否进入空闲状态。  
  
 如果 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 未进入空闲状态，则会按相反顺序执行，因为安排的活动作为堆栈来处理，最后安排的活动最先执行。例如，如果在 <xref:System.Activities.Statements.ParallelForEach%601> 中有一个集合 {1,2,3,4}，并使用 **WriteLine** 作为写出值的 Body。则会在控制台中依次打印出 4、3、2、1。这是因为 **WriteLine** 未进入空闲状态，因此在安排 4 个 **WriteLine** 活动之后，会使用堆栈行为（先进后出）执行这些活动。  
  
 但是如果 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 中有会进入空闲状态的活动，如 <xref:System.ServiceModel.Activities.Receive> 活动或 <xref:System.Activities.Statements.Delay> 活动，那么就不需要等待它们完成。<xref:System.Activities.Statements.ParallelForEach%601> 转至下一个预定的身体活动，并尝试执行它。如果该活动也进入空闲状态，则 <xref:System.Activities.Statements.ParallelForEach%601> 将再移到下一个 Body 活动。  
  
### 使用 ParallelForEach\<T\> 活动设计器  
 **“ParallelForEach\<T\>”**活动设计器可在**“工具箱”**的**“控制流”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左侧的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“ParallelForEach\<T\>”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动设计器的任何位置，例如**“Sequence”**活动设计器内。将该活动设计器放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中之后，它会创建一个 <xref:System.Activities.Statements.ParallelForEach%601> 活动，该活动默认情况下包含的 <xref:System.Activities.Activity.DisplayName%2A> 为 **ParallelForEach\<Int32\>.** 。  
  
### 工作流设计器中的 ParallelForEach\<T\> 属性  
 下表列出最有用的 <xref:System.Activities.Statements.ParallelForEach%601> 活动属性并说明如何在设计器中使用它们。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活动设计器在标头中的友好显示名称。默认值为 **ParallelForEach\<Int32\>**。可以根据需要在**“属性”**网格或直接在活动设计器标头中编辑该值。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|要为集合中的每一项执行的活动。若要添加 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 活动，请将活动从工具箱拖放到**“ParallelForEach\<T\>”**活动设计器上带提示文本“在此处放置活动”的**“Body”**框中。|  
|**TypeArgument**|True|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A> 集合中的项的类型，由泛型参数 *T* 指定。默认情况下，**TypeArgument** 设置为 **Int32**。若要更改**“ParallelForEach\<T\>”**活动设计器中的类型 T，请在属性网格中更改**“TypeArgument”**组合框的值。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|要循环访问的项的集合。若要设置 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>，请在**“ForEach\<T\>”**活动设计器上带提示文本“输入 VB 表达式”的**“值”**框或在**“属性”**窗口的**“值”**框中键入 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 表达式。|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||在每个迭代完成后计算。如果其计算结果为 true，则取消已安排的挂起的迭代。如果未设置此属性，则所有安排的语句都将执行，直至完成为止。|  
  
 默认情况下，循环迭代器是命名项。可在**“ParallelForEach\<T\>”**活动设计器的**“ForEach”**框中更改迭代器变量的名称。循环迭代器可在 <xref:System.Activities.Statements.ParallelForEach%601> 活动的子级中的表达式中使用。  
  
## 请参阅  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [控制流](../workflow-designer/control-flow-activity-designers.md)