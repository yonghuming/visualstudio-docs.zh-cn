---
title: "如何： 定义和使用工作流设计器中的活动委托 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: 106ef4e7ca41fc181cc305f99e5abfce2abd825e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>如何：在工作流设计器中定义和使用活动委托
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 包括用于 <xref:System.Activities.Statements.InvokeDelegate> 活动的新的现成可用的设计器。  此设计器可用于将委托分配给从 <xref:System.Activities.ActivityDelegate> 派生的活动，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。  
  
### <a name="define-an-activity-delegate"></a>定义活动委托  
  
1.  在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，选择**文件**，**新建**，**项目**。 选择**工作流**在左侧，节点和**工作流控制台应用程序**右侧的模板。 将项目 （如果需要），然后单击**确定**。  
  
2.  右键单击该项目中**解决方案资源管理器**和选择**添加**，**新建项...**.选择**工作流**在左侧，节点和**活动**右侧的模板。 将新活动**MyForEach.xaml**单击**确定**。 将在工作流设计器中打开活动。  
  
3.  在工作流设计器中，单击**参数**选项卡。  
  
4.  单击**创建自变量**。 将新参数命名**项**。  
  
5.  在**自变量类型**列中，选择**[T] 的数组**。  
  
6.  在类型浏览器中，选择**对象**。 Click **Ok**.  
  
7.  单击**创建自变量**试。 将新参数命名**正文**。 在**方向**对于新的自变量，选择列**属性**。  
  
8.  在自变量类型列中，选择**浏览类型...**  
  
9. 在类型浏览器中，输入**ActivityAction**中**类型名称**字段。 选择**ActivityAction\<T >**树视图中。 选择**对象**显示分配类型的下拉列表中**ActivityAction\<对象 >**到自变量。  
  
10. 拖动<xref:System.Activities.Statements.While>活动从**控制流**一部分工具箱拖到设计器图面。  
  
11. 选择<xref:System.Activities.Statements.While>活动，然后选择**变量**选项卡。  
  
12. 选择**创建变量**。 将新的变量命名**索引**。  
  
13. 在**变量类型**列中，选择**Int32**。 保留**作用域**作为**时**，和**默认**列保留为空。  
  
14. 设置**条件**属性<xref:System.Activities.Statements.While>活动**索引 < Items.Length;**。  
  
15. 拖动<xref:System.Activities.Statements.InvokeDelegate>活动从**基元**一部分工具箱拖到**正文**的<xref:System.Activities.Statements.While>活动。  
  
16. 选择**正文**在委托下拉列表。  
  
17. 在**属性**网格<xref:System.Activities.Statements.InvokeDelegate>活动，单击**...**按钮**委托自变量**属性。  
  
18. 在**值**自变量名为列**参数**，输入**Items [Index]**。 单击**确定**关闭**DelegateArguments**对话框。  
  
19. 将 <xref:System.Activities.Statements.Assign> 活动拖到 <xref:System.Activities.Statements.InvokeDelegate> 活动的水平线下。 <xref:System.Activities.Statements.Assign>将创建活动，和一个<xref:System.Activities.Statements.Sequence>将自动创建活动以包含中的两个活动**正文**部分**MyForEach**活动。 需要序列，因为**正文**部分只能包含单个活动。 自动创建新的 <xref:System.Activities.Statements.Sequence> 活动是 [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 的一个新功能。  
  
20. 设置**到**属性<xref:System.Activities.Statements.Assign>活动**索引**。 设置**值**属性**分配**活动**index + 1**。  
  
 自定义**MyForEach**活动现在将调用一次用于传递给它通过每个值的任意活动**项**集合，集合中作为活动的输入的值。  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流中的自定义活动  
  
1.  通过按生成项目**Ctrl + Shift + B**。  
  
2.  在**解决方案资源管理器**，打开**Workflow1.xaml**设计器中。  
  
3.  拖动**MyForEach**活动从工具箱拖到设计器图面。 该活动将位于工具箱的某个部分中，其名称与项目名称相同。  
  
4.  设置**项**属性**MyForEach**活动**新对象 [] {1，"abc"}**。  
  
5.  拖动<xref:System.Activities.Statements.WriteLine>活动从**基元**一部分工具箱拖到**委托： 正文**部分**MyForEach**活动。  
  
6.  设置**文本**属性<xref:System.Activities.Statements.WriteLine>活动**Argument.ToString()**。  
  
 当执行工作流时，控制台将显示以下信息：  
  
 **1**   
**abc**