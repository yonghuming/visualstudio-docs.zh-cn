---
title: "如何：在工作流设计器中定义和使用活动委托 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "sdanie"
manager: "erikre"
---
# 如何：在工作流设计器中定义和使用活动委托
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 包括 <xref:System.Activities.Statements.InvokeDelegate> 活动的新现成可用的设计器。 此设计器可用于指定给派生自 <xref:System.Activities.ActivityDelegate> 的委托，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。  
  
### 定义活动委托  
  
1.  在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中，选择**“文件”**、**“新建”**、**“”项目**。选择左边的**“工作流”**节点和右边的**“工作流控制台应用程序”**模版。将项目命名为 项目（如果需要）并单击**“确定”**。  
  
2.  在**“解决方案资源管理器”**中，右击项目，然后选择**“添加”**，**新项…**。选择左边的**“工作流”**节点和右边的**“活动”**模版。命名新活动 **MyForEach.xaml**，然后单击**“确定”**。在工作流设计器中打开活动。  
  
3.  在工作流设计器中单击**“参数”**选项卡。  
  
4.  单击**“创建参数”**。名称新参数**项**。  
  
5.  在**“参数类型”** 列中，选择 **“\[T\] 的阵列”**。  
  
6.  在类型浏览器中，选择**“对象”**。单击**“确定”**。  
  
7.  再次单击**“创建参数”**。名称新参数**正文**。在新参数的**“方向”**列中，请选择**“属性”**。  
  
8.  在参数类型列中，选择 **“浏览类型…”浏览**  
  
9. 在类型浏览器中，输入**“类型名称”**字段中的 **ActivityAction**。 在树视图中选择 **ActivityAction\<T\>**。在出现类型 **ActivityAction\<Object\>** 分配给参数的下拉列表中，选择**“对象”**。  
  
10. 将 <xref:System.Activities.Statements.While> 活动从工具箱的**“控制流”**部分拖放到设计器图面中。  
  
11. 选择 <xref:System.Activities.Statements.While> 活动，然后选择**“变量”**选项卡。  
  
12. 选择**“创建变量”**。命名新变量**索引**。  
  
13. 在**“变量类型”** 列中，选择 **Int32**。 将**“范围”** 保留为 **While**，和**“默认”**列保留为空。  
  
14. 将 <xref:System.Activities.Statements.While> 活动的**“条件”**属性设置为 **index \< Items.Length;**。  
  
15. 将 <xref:System.Activities.Statements.InvokeDelegate> 活动从工具箱的**“基元”**部分拖放到 <xref:System.Activities.Statements.While> 活动的**“正文”**。  
  
16. 在委托下拉列表中选择**“正文”**。  
  
17. 在网格的 <xref:System.Activities.Statements.InvokeDelegate> 活动的**“属性”**栅格中，请单击**“委托参数”**属性中的**“…”**按钮在属性。  
  
18. 在命名**“参数”**的参数的**“值”**列中，输入**项目\[索引\]**。单击**“确定”**关闭**“DelegateArguments”**对话框。  
  
19. 拖到 <xref:System.Activities.Statements.InvokeDelegate>活动下水平线上的 <xref:System.Activities.Statements.Assign> 活动。将创建 <xref:System.Activities.Statements.Assign>活动，并且 <xref:System.Activities.Statements.Sequence> 活动将自动创建以包含 **MyForEach** 活动的**“正文”**部分中的两个活动。 自**“正文”**部分仅可以包含单一活动起需要序列。自动创建新的 <xref:System.Activities.Statements.Sequence> 活动是 [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 的一个新功能。  
  
20. 将  <xref:System.Activities.Statements.Assign> 活动的**“To”**属性设置为**索引**。将**“Assign”**活动的**“值”**属性设置为 **index\+1**。  
  
 通过其中具有作为活动的输入的值的 **Items** 集合，自定义 **MyForEach** 活动现为传递到该活动的每个值调用一次任意活动。  
  
### 使用工作流中的自定义活动  
  
1.  通过按 **Ctrl\+Shift\+B** 生成项目。  
  
2.  在**“解决方案资源管理器”**中，打开设计器中的 **Workflow1.xaml**。  
  
3.  将 **MyForEach** 活动从工具箱拖到设计器图面。活动将位于工作项部分中，与项目的名称相同。  
  
4.  将 **MyForEach**活动的**“项目”**属性设置为**新对象\[\] {1，"abc"}**。  
  
5.  将 <xref:System.Activities.Statements.WriteLine> 活动从工具箱的**“基元”**部分拖放到 **MyForEach** 活动的**“委托正文”**部分。  
  
6.  将<xref:System.Activities.Statements.WriteLine> 活动的**“文本”**属性设置为 **Argument.ToString\(\)**。  
  
 当执行工作流时，控制台将显示以下信息：  
  
 **1**   
**abc**