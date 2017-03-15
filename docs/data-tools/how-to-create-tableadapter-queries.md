---
title: "如何：创建 TableAdapter 查询 | Microsoft Docs"
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
  - "数据 [Visual Studio], TableAdapter 查询"
  - "查询 [Visual Studio], 创建"
  - "查询 [Visual Studio], TableAdapter"
  - "TableAdapter, 创建查询"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：创建 TableAdapter 查询
TableAdapter 查询是应用程序可以对数据库执行的 SQL 语句或存储过程。  
  
 按照应用程序的需要可将任意多的查询添加到 TableAdapter。  TableAdapter 查询显示为 TableAdapter 上的方法。  在创建采用表示城市值的参数的名为 `FillByCity` 的查询时，该查询被添加到 TableAdapter。  该查询作为类型化方法添加，该方法采用正确类型的参数作为变量 \-\- 在此示例中是一个表示城市值的字符串。  可以像调用任何对象的任何方法那样调用 TableAdapter 查询。  例如，下面的代码执行 `FillByCity` 查询，并用城市值为 `Seattle` 的所有客户填充 `Customers` 表：  
  
 [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
 TableAdapter 查询可以填充数据表（`Fill` 和 `FillBy` 查询）或返回以通过查询返回的数据填充的新数据表（`GetData` 和 `GetDataBy` 查询）。  
  
 通过运行 [TableAdapter 查询配置向导](../data-tools/editing-tableadapters.md)，您可以将查询添加到现有的 TableAdapter。  （右击任意 TableAdapter 并选择**“添加查询”**。）  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 在数据集设计器中创建查询  
  
#### 在数据集设计器中向 TableAdapter 添加查询  
  
1.  在**“数据集设计器”**中打开一个数据集。  有关更多信息，请参见[如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  右击所需的 TableAdapter，然后选择**“添加查询”**。  
  
     \- 或 \-  
  
3.  将一个**“查询”**从**“工具箱”**的**“数据集”**选项卡拖动到设计器上的表中。  
  
     **“TableAdapter 查询配置向导”**将打开。  
  
4.  完成向导；该查询即被添加到 TableAdapter。  
  
## 在 Windows 应用程序中的窗体上直接创建查询  
 如果在窗体上有一个 TableAdapter 的实例，则可以使用 [“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) 添加查询，该对话框向窗体添加接受查询所需的任何输入参数的 <xref:System.Windows.Forms.ToolStrip> 控件，以及一个运行查询的按钮。  
  
#### 使用“搜索条件”对话框向 TableAdapter 添加查询  
  
1.  在组件栏中选择一个 TableAdapter。  
  
2.  单击该 TableAdapter 的智能标记，然后选择**“添加查询”**。  
  
3.  完成该对话框，该查询即被添加到 TableAdapter。  有关更多信息，请参见 [“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
## 请参阅  
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [如何：编辑 TableAdapter 查询](../data-tools/how-to-edit-tableadapter-queries.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [如何：使用 Windows 窗体 BindingNavigator 控件定位数据](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [演练：创建带有多个查询的 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)