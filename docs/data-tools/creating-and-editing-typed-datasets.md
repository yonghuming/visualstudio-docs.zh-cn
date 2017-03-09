---
title: "创建和编辑类型化数据集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], Dataset Designer — 数据集设计器"
  - "Dataset Designer — 数据集设计器"
  - "数据集 [Visual Basic], 可视设计器"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 创建和编辑类型化数据集
“数据集设计器”是一套可视化工具，用于创建和编辑类型化数据集和组成数据集的各个项。  
  
 **“数据集设计器”**提供类型化数据集所包含对象的可视表示形式。  可以使用**“数据集设计器”**创建和修改 [TableAdapter](../data-tools/tableadapter-overview.md)、[TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)、<xref:System.Data.DataTable>、<xref:System.Data.DataColumn> 和 <xref:System.Data.DataRelation>。  
  
 若要打开**“数据集设计器”**，请在**“解决方案资源管理器”**中双击一个数据集，或是在**“数据源”**窗口中右击一个数据集并单击**“使用设计器编辑数据集”**。  有关详细信息，请参阅[如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  使用**“添加新项”**对话框添加新的 <xref:System.Data.DataSet> 项会打开**“数据集设计器”**，其中包含一个空数据集可供编辑。  
  
> [!NOTE]
>  **“数据集设计器”**可用于扩展数据集的功能。  双击设计图面或右击并选择**“查看代码”**可创建分部类文件，在该文件中可以向数据集添加不会被设计器更改或删除的代码。  有关扩展 TableAdapter 功能的信息，请参见[如何：扩展 TableAdapter 的功能](../data-tools/extend-the-functionality-of-a-tableadapter.md)。  
  
 下表列出了可使用**“数据设计器”**完成的常规任务。  
  
|若要|请参见|  
|--------|---------|  
|创建 TableAdapter|[如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|  
|编辑 TableAdapter|[如何：编辑 TableAdapter](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|创建 TableAdapter 查询|[如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)|  
|编辑 TableAdapter 查询|[如何：编辑 TableAdapter 查询](../data-tools/how-to-edit-tableadapter-queries.md)|  
|创建 <xref:System.Data.DataTable>|[如何：创建数据表](../data-tools/how-to-create-data-tables.md)|  
|编辑 <xref:System.Data.DataTable>|[设计数据表](../data-tools/designing-datatables.md)|  
|创建 <xref:System.Data.DataColumn>|[如何：向数据表添加列](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|创建两个 <xref:System.Data.DataTable> 之间的关系|[如何：使用数据集设计器创建 DataRelation](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|扩展数据集的功能|[如何：扩展数据集的功能](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|向数据表的 <xref:System.Data.DataTable.ColumnChanging> 事件添加验证|[如何：在列更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|向数据表的 <xref:System.Data.DataTable.RowChanging> 事件添加验证|[如何：在行更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## 在设计图面上创建对象  
 可以通过添加和编辑组成数据集的各个对象创建数据集。  下表提供对**“工具箱”**的**“数据集”**选项卡中可以被拖动到设计图面上的不同对象的解释：  
  
|对象|描述|  
|--------|--------|  
|TableAdapter|包含一个数据命令的集合和一个数据连接，它们用于与基础数据库通信和填充数据表。  有关更多信息，请参见[TableAdapter 概述](../data-tools/tableadapter-overview.md)和[如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。|  
|查询|TableAdapter 查询是执行 SQL 语句和存储过程的强类型方法。  运行 TableAdapter 查询可用数据填充数据表或执行其他数据库任务。  有关详细信息，请参阅[如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)。  将查询拖动到表上可将该查询添加到该表，而将查询拖动到**“数据集设计器”**的空白区域上会创建全局查询。  有关详细信息，请参阅[如何：向数据集添加全局查询](../data-tools/how-to-add-global-queries-to-a-tableadapter.md)。|  
|<xref:System.Data.DataTable>|表示内存中从数据库返回的行的集合。|  
|关系 \(<xref:System.Data.DataRelation>\)|表示两个 <xref:System.Data.DataTable> 之间的父子关系。  有关更多信息，请参见[介绍 DataRelation 对象](../Topic/Introduction%20to%20DataRelation%20Objects.md)和[演练：创建数据表之间的关系](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)。|  
  
> [!NOTE]
>  只有当数据集被创建后，“数据集设计器” 连接到一个基础数据库；设计器不会自动检测数据库的后续更改。  若要刷新现有 .xsd ，请重新运行“配置向导”。  如果表关系已更改，移除并重新添加 .xsd 的相关表。  
  
## LINQ to Dataset  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] 支持对 <xref:System.Data.DataSet> 对象中的数据执行[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)。  有关详细信息，请参阅[LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)。  
  
## 请参阅  
 [演练：使用数据集设计器创建数据集](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [演练：创建带有多个查询的 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [演练：在数据集设计器中创建数据表](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [演练：创建数据表之间的关系](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [“数据源”窗口](../Topic/Data%20Sources%20Window.md)   
 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)