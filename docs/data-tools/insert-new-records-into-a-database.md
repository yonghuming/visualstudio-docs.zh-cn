---
title: "如何：将新记录插入数据库 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "数据 [Visual Studio], 保存"
  - "数据库, 插入新记录到"
  - "记录, 插入"
  - "保存数据"
  - "TableAdapter, 插入新记录到"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将新记录插入数据库
若要将新记录插入数据库中，您可以使用 `TableAdapter.Update` 方法，或 TableAdapter 的 DBDirect 方法之一（特别是 `TableAdapter.Insert` 方法）。  有关更多信息，请参见 [TableAdapter 概述](../data-tools/tableadapter-overview.md)。  
  
 如果您的应用程序不使用 TableAdapters，您就可以使用命令对象与数据库交互并插入新记录到其中（例如，<xref:System.Data.SqlClient.SqlCommand>）。  
  
 当应用程序使用数据集存储数据时，请使用 `TableAdapter.Update` 方法。  `Update` 方法会将所有更改（包括更新、插入以及删除）发送到数据库中。  
  
 当应用程序使用对象存储数据时，或者您要对在数据库中创建新记录进行更好的控制时，请使用 `TableAdapter.Insert` 方法。  
  
 如果 TableAdapter 没有 `Insert` 方法，则意味着或者该 TableAdapter 是为使用存储过程而配置的，或者其 `GenerateDBDirectMethods` 属性已被设置为 `false`。  尝试从[“数据集设计器”](../data-tools/creating-and-editing-typed-datasets.md)内将 TableAdapter 的 `GenerateDBDirectMethods` 属性设置为 `true`，然后保存该数据集以重新生成 TableAdapter。  如果 TableAdapter 仍没有 `Insert` 方法，则该表可能没有提供足够的架构信息以区分各行（例如，表中未设置主键）。  
  
## 使用 TableAdapter 插入新记录  
 根据应用程序的需要，TableAdapter 提供了将新记录插入数据库的不同方法。  
  
 如果应用程序使用数据集存储数据，则可以完全将新记录添加到数据集中所需的 <xref:System.Data.DataTable>，然后调用 `TableAdapter.Update` 方法。  `TableAdapter.Update` 方法得到 <xref:System.Data.DataTable> 中的所有更改，并将这些更改发送到数据库中（包括已修改的记录和删除的记录）。  
  
#### 使用 TableAdapter.Update 方法将新记录插入数据库  
  
1.  通过创建新的 <xref:System.Data.DataRow> 并将它添加到 <xref:System.Data.DataTable.Rows%2A> 集合中，可将新记录添加到所需的 <xref:System.Data.DataTable> 中。  有关更多信息，请参见[如何：向数据表中添加行](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md)。  
  
2.  将新行添加到 <xref:System.Data.DataTable> 后，请调用 `TableAdapter.Update` 方法。  通过传入完整的 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 数组或单个 <xref:System.Data.DataRow>，您可以控制要更新的数据量。  
  
     下面的代码显示如何将新记录添加到 <xref:System.Data.DataTable> 中，然后调用 `TableAdapter.Update` 方法将新行保存到数据库中。  （此示例使用 Northwind 数据库的 `Region` 表。）  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 如果应用程序使用对象存储应用程序中的数据，您就可以使用 `TableAdapter.Insert` 方法直接在数据库中创建新行。  `Insert` 方法接受将每一列的单个值作为参数。  调用此方法用传入的参数值将新记录插入到数据库。  
  
 以下过程使用 Northwind 数据库的 `Region` 表作为示例。  
  
#### 使用 TableAdapter.Insert 方法将新记录插入到数据库  
  
-   调用 TableAdapter 的 `Insert` 方法，为每一列传入值作为参数。  
  
    > [!NOTE]
    >  如果没有实例可用，请实例化您要使用的 TableAdapter。  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## 使用命令对象插入新记录  
 下面的示例使用命令对象直接将新记录插入到数据库。  有关使用命令对象执行命令和存储过程的更多信息，请参见[将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)。  
  
 以下过程使用 Northwind 数据库的 `Region` 表作为示例。  
  
#### 使用命令对象将新记录插入到数据库  
  
-   创建新的命令对象，并设置它的 `Connection`、`CommandType` 和 `CommandText` 属性。  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## .NET Framework 安全性  
 您必须有访问正尝试连接到的数据库的权限，以及在所需表中执行插入的权限。  
  
## 请参阅  
 [如何：删除数据库中的记录](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [如何：更新数据库中的记录](../data-tools/how-to-update-records-in-a-database.md)   
 [如何：将数据从对象保存到数据库](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)   
 [检索“标识”或“自动编号”值](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)