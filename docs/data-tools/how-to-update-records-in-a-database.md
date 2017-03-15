---
title: "如何：更新数据库中的记录 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "数据库, 更新"
  - "记录, 编辑"
  - "记录, 更新"
  - "TableAdapter.Update 方法"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：更新数据库中的记录
可以使用 `TableAdapter.Update` 方法更新（编辑）数据库中的记录。  `TableAdapter.Update` 方法根据传入的参数提供了若干次执行不同操作的重载。  了解调用这些不同方法签名的结果非常重要。  
  
> [!NOTE]
>  如果您的应用程序不使用 TableAdapter，您就可以使用命令对象更新数据库中的记录（例如，<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>）。  有关使用命令对象更新数据的更多信息，请参见下面的“使用命令对象更新记录”。  
  
 下表描述了各种 `TableAdapter.Update` 方法的行为：  
  
|方法|说明|  
|--------|--------|  
|`TableAdapter.Update(DataTable)`|尝试将 <xref:System.Data.DataTable> 中的所有更改保存到数据库中。  （这包括从表中移除所有删除的行、将插入的行添加到表中、更新表中已更改的所有行。）|  
|`TableAdapter.Update(DataSet)`|虽然该参数带有一个数据集，但 TableAdapter 仍尝试将 TableAdapter 的关联 <xref:System.Data.DataTable> 中的所有更改保存到数据库中。  （这包括从表中移除所有删除的行、将插入的行添加到表中、更新表中已更改的所有行。） **Note:**  TableAdapter 的关联 <xref:System.Data.DataTable> 是最初配置 TableAdapter 时创建的 <xref:System.Data.DataTable>。|  
|`TableAdapter.Update(DataRow)`|尝试将指示 <xref:System.Data.DataRow> 中的更改保存到数据库中。|  
|`TableAdapter.Update(DataRows())`|尝试将 <xref:System.Data.DataRow> 数组中任意行中的更改保存到数据库中。|  
|`TableAdapter.Update("new column values", "original column values")`|尝试保存由原始列值标识的单行中的更改。|  
  
 通常，当应用程序使用数据集以独占方式存储数据时，您使用的是带有 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 的 `TableAdapter.Update` 方法。  
  
 通常，当应用程序使用对象存储数据时，您使用的是带有列值的 `TableAdapter.Update` 方法。  
  
 如果 TableAdapter 没有带列值的 `Update` 方法，就表示已将 TableAdapter 配置为使用存储过程，或者已将它的 `GenerateDBDirectMethods` 属性设置为 `false`。  尝试从[“数据集设计器”](../data-tools/creating-and-editing-typed-datasets.md)内将 TableAdapter 的 `GenerateDBDirectMethods` 属性设置为 `true`，然后保存该数据集以重新生成 TableAdapter。  如果 TableAdapter 仍没有带列值的 `Update` 方法，该表就可能没有提供足够多的架构信息以区分各行（例如，未在表中设置任何主键）。  
  
## 使用 TableAdapter 更新现有记录  
 根据应用程序的需要，TableAdapter 提供了更新数据库中记录的不同方法。  
  
 如果应用程序使用数据集存储数据，则可以在所需的 <xref:System.Data.DataTable> 中简单地更新记录，然后调用 `TableAdapter.Update` 方法并传入 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 或 <xref:System.Data.DataRow> 数组。  上表描述了不同的 `Update` 方法。  
  
#### 用带有 DataSet、DataTable、DataRow 或 DataRows\(\) 的 TableAdapter.Update 方法更新数据库中的记录  
  
1.  通过直接编辑 <xref:System.Data.DataTable> 中的 <xref:System.Data.DataRow>，编辑所需的 <xref:System.Data.DataTable> 中的记录。  有关更多信息，请参见 [如何：编辑数据表中的行](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md)。  
  
2.  在 <xref:System.Data.DataTable> 中对行进行编辑后，请调用 `TableAdapter.Update` 方法。  通过传入完整的 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 数组或单个 <xref:System.Data.DataRow>，您可以控制要更新的数据量。  
  
     下面的代码显示如何编辑 <xref:System.Data.DataTable> 中的记录，然后调用 `TableAdapter.Update` 方法将更改保存到数据库中。  （此示例使用 Northwind 数据库 Region 表。）  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 如果应用程序使用对象存储应用程序中的数据，您就可以使用 TableAdapter 的 `DBDirect` 方法将数据从对象中直接发送到数据库。  这些方法可让您将各列的单个值传递为方法参数。  调用此方法用传入该方法的列值更新数据库中的现有记录。  
  
 以下过程使用 Northwind `Region` 表作为示例。  
  
#### 使用带有列值的 TableAdapter.Update 方法更新数据库中的记录  
  
-   调用 TableAdapter 的 `Update` 方法，以参数的形式为每一列传入新值和原始值。  
  
    > [!NOTE]
    >  如果没有实例可用，请实例化您要使用的 TableAdapter。  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## 使用命令对象更新记录  
 下面的示例使用命令对象直接更新数据库中的现有记录。  有关使用命令对象执行命令和存储过程的更多信息，请参见[将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)。  
  
 以下过程使用 Northwind `Region` 表作为示例。  
  
#### 使用命令对象更新数据库中的现有记录  
  
-   创建新的命令对象；设置它的 `Connection`、`CommandType` 和 `CommandText` 属性；然后打开一个连接，并执行该命令。  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## .NET Framework 安全性  
 您必须具有访问正尝试连接到的数据库的权限，以及更新所需表中记录的权限。  
  
## 请参阅  
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [如何：删除数据库中的记录](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [如何：将新记录插入数据库](../data-tools/insert-new-records-into-a-database.md)   
 [如何：将数据从对象保存到数据库](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)