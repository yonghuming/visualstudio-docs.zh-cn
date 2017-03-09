---
title: "如何：创建和执行返回单个值的 SQL 语句 | Microsoft Docs"
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
  - "数据命令, 返回标量值"
  - "数据读取器"
  - "DataReader 对象"
  - "标量值"
  - "SQL 语句, 数据命令"
  - "存储过程, 返回单个值"
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：创建和执行返回单个值的 SQL 语句
若要执行返回单个值的 SQL 语句，可以运行一个配置为运行 SQL 语句的 TableAdapter 查询（如 `CustomersTableAdapter.CustomerCount()`）。  
  
 如果应用程序不使用 TableAdapter，请调用命令对象上的 `ExecuteScalar` 方法，将其 `CommandType` 属性设置为 <xref:System.Data.CommandType>。  （“命令对象”是指您的应用程序正在使用的 .NET Framework 数据提供程序的特定命令。[](../Topic/.NET%20Framework%20Data%20Providers.md) 例如，如果应用程序使用的是用于 SQL Server 的 .NET Framework 数据提供程序，则该命令对象为 <xref:System.Data.SqlClient.SqlCommand>。）  
  
 下面的示例演示如何使用 TableAdapters 或命令项目执行从数据库返回单个值的 SQL 语句。  有关使用 TableAdapter 和命令进行查询的更多信息，请参见 [用数据填充数据集](../data-tools/fill-datasets-by-using-tableadapters.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 使用 TableAdapter 执行返回单个值的 SQL 语句  
 此示例演示如何使用 [TableAdapter 查询配置向导](../data-tools/editing-tableadapters.md) 创建 TableAdapter 查询，然后提供有关如何声明 TableAdapter 的实例并执行查询的信息。  
  
#### 使用 TableAdapter 创建返回单个值的 SQL 语句  
  
1.  在**“数据集设计器”**中打开一个数据集。  有关更多信息，请参见[如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  如果还没有 TableAdapter，请创建一个。  有关创建 TableAdapter 的更多信息，请参见 [如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
3.  如果在 TableAdapter 上已有一个使用 SQL 语句返回单个值的查询，则跳到下一步骤，“声明 TableAdapter 的实例并执行查询”。否则，请继续步骤 4 创建一个返回单个值的新查询。  
  
4.  右击所需的 TableAdapter，然后使用快捷菜单添加查询。  
  
     **“TableAdapter 查询配置向导”**将打开。  
  
5.  保留**“使用 SQL 语句”**的默认值，然后单击**“下一步”**。  
  
6.  选择**“选择\(返回单个值\)”**选项，然后单击**“下一步”**。  
  
7.  键入 SQL 语句，或借助**“查询生成器”**创建一条 SQL 语句，然后单击**“下一步”**。  
  
8.  为该查询提供名称。  
  
9. 完成向导；该查询即被添加到 TableAdapter。  
  
10. 生成您的项目。  
  
#### 声明 TableAdapter 的实例并执行查询  
  
1.  声明一个 TableAdapter 实例，该实例包含要执行的查询。  
  
    -   若要使用设计时工具创建实例，请从**“工具箱”**拖动所需的 TableAdapter。  （现在，项目中的组件将出现在**“工具箱”**中，位于与项目名称匹配的标题下。）如果**“工具箱”**中没有出现 TableAdapter，则可能需要生成您的项目。  
  
         \- 或 \-  
  
    -   要在代码中创建实例，请使用您的 <xref:System.Data.DataSet> 和 TableAdapter 的名称替换下面的代码。  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapter 实际上并不在其关联数据集类内。  每个数据集在其各自命名空间中均有一个相应的 TableAdapter 集合。  例如，如果有一个名为 `SalesDataSet` 的数据集，就会有一个包含其 TableAdapter 的 `SalesDataSetTableAdapters` 命名空间。  
  
2.  请按照在代码中调用任何其他方法的方式调用查询。  查询是 TableAdapter 上的一个方法。  用您的 TableAdapter 和查询的名称替换下面的代码。  还会需要传入查询所需的任何参数，并对返回值进行一些操作（例如，将其指定给一个变量）。  如果不能确定查询是否需要参数，或者需要什么参数，请通过 IntelliSense 查看该查询所需的签名。  根据查询是否带有参数，代码可能会类似于以下示例之一：  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  可能会需要将查询的返回值分配到一个变量。  返回单个值的 TableAdapter 查询将返回一个基于该查询的数据类型（与返回一个对象的 `ExecuteScalar` 方法相反）。  例如，如果 TableAdapter 查询选择数据类型是整数的单个列，则查询的返回值也是整数。  如果列允许空值，则返回值是可以为 null 的类型之一（例如 `Nullable(Of Integer)`）。  有关可以为 null 的类型的更多信息，请参见 <xref:System.Nullable>。  声明一个 TableAdapter 实例并执行一个查询的完整代码可参见下面的示例（此示例假定返回值为整数，根据查询返回的数据类型对代码进行调整）：  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.vb)]  
  
## 使用命令对象执行返回单个值的 SQL 语句  
 下面的示例演示如何创建命令并执行返回单个值的 SQL 语句。  有关设置和获取命令参数值的信息，请参见 [如何：设置和获取命令对象的参数](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)。  
  
 此示例使用 <xref:System.Data.SqlClient.SqlCommand> 对象并且需要：  
  
-   对 <xref:System>、<xref:System.Data> 和 <xref:System.Xml> 命名空间的引用。  
  
-   名为 `SqlConnection1` 的数据连接。  
  
-   `SqlConnection1` 所连接到的数据源中名为 `Customers` 的表。  （否则，您需要一条对您的数据源有效的 SQL 语句。）  
  
#### 使用 DataCommand 创建返回单个值的 SQL 语句  
  
-   将下面的代码添加到要用于执行该代码的方法中。  通过调用命令（例如，<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>）的 `ExecuteScalar` 方法可返回单个值。  此数据返回到 <xref:System.Object> 中。  
  
     [!code-cs[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.vb)]  
  
## .NET Framework 安全性  
 此应用程序要求访问数据库和执行 SQL 语句的权限。  
  
## 请参阅  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)   
 [如何：编辑 TableAdapter 查询](../data-tools/how-to-edit-tableadapter-queries.md)   
 [如何：使用数据填充数据集](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [用数据填充数据集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [如何：设置和获取命令对象的参数](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)