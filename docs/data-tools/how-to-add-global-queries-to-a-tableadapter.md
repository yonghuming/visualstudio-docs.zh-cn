---
title: "如何：向数据集添加全局查询 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], TableAdapter"
  - "数据集 [Visual Basic], 全局函数"
  - "数据集 [Visual Basic], 标量函数"
  - "全局函数, 数据集"
  - "查询 [Visual Studio], TableAdapter"
  - "标量函数, 数据集"
  - "TableAdapter 查询"
  - "TableAdapter 查询配置向导"
  - "TableAdapter, 全局查询"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：向数据集添加全局查询
“全局查询”是返回单个（标量）值或不返回任何值的 SQL 查询。  通常，全局函数执行数据库操作，如插入、更新、删除和信息的聚合（如返回某表中客户的计数或特定订单中所有项的总价）。  
  
 可以通过从**“数据集设计器”**运行**“TableAdapter 查询配置向导”**添加全局查询。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 向数据集添加全局查询  
  
1.  在**“数据集设计器”**中打开一个数据集。  有关更多信息，请参见[如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  将一个**“查询”**从**“工具箱”**的**“数据集”**选项卡拖动到**“数据集设计器”**上的空白区域。  
  
     [TableAdapter 查询配置向导](../data-tools/editing-tableadapters.md)将打开。  
  
3.  选择查询要使用的一个连接。  可以从列表中选择，也可以创建一个新连接。  如果创建新连接，则可以选择将它保存到应用程序配置文件中。  有关更多信息，请参见[如何：保存和编辑连接字符串](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md)。  
  
4.  选择是使用 SQL 语句还是存储过程。  
  
5.  选择要使用的存储过程，或是在向导的**“选择查询类型”**页上选择需要的查询类型，然后单击**“下一步”**。  
  
6.  提供一个执行所需任务的查询（如 `SELECT COUNT(*) AS CustomerCount FROM Customers`）。  
  
    > [!NOTE]
    >  直接将查询拖动到**“数据集设计器”**以创建一个只返回单个标量值的方法。  尽管所选择的查询或存储过程可以返回多个值，但通过向导创建的方法将只返回单个值。  例如，查询可能返回所返回数据的第一行的第一列。  
  
7.  完成向导；该查询即被添加到**“数据集设计器”**。  有关运行查询的信息，请参见 [如何：执行 TableAdapter 查询](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md)。  
  
## 请参阅  
 [如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [如何：使用 Windows 窗体 BindingNavigator 控件定位数据](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)