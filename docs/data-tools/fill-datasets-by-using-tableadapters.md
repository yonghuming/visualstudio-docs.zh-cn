---
title: "用数据填充数据集 | Microsoft Docs"
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
  - "数据 [Visual Studio], 数据集"
  - "数据 [Visual Studio], 检索"
  - "数据检索"
  - "数据集 [Visual Basic]"
  - "数据集 [Visual Basic], 填充"
  - "数据集 [Visual Basic], 加载数据"
  - "检索数据"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用数据填充数据集
用于执行 Transact\-SQL 查询和用于填充数据集的典型 Visual Studio 机制是 TableAdapter。  
  
 可以使用 TableAdapter 或命令对象对数据源执行 SQL 语句或存储过程（例如 <xref:System.Data.SqlClient.SqlCommand>）。  若要将数据加载到使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的设计工具创建的数据集中，请使用 TableAdapter。  若要将数据加载到以编程方式创建的数据集，请使用数据适配器。  如果应用程序不使用数据集，可以使用命令对象直接对数据库执行 SQL 语句或存储过程。  
  
 以下主题提供有关在 Visual Studio 中用数据填充数据集的详细信息：  
  
|主题|说明|  
|--------|--------|  
|[如何：使用数据填充数据集](../data-tools/how-to-fill-a-dataset-with-data.md)|详细介绍如何使用 TableAdapters 和 DataAdapters 将数据加载到数据集。|  
|[如何：创建和执行返回行的 SQL 语句](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)|详细介绍如何使用 TableAdapter 查询和 Command 对象创建和执行返回行的 SQL 语句。|  
|[如何：创建和执行返回单个值的 SQL 语句](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)|详细介绍如何使用 TableAdapter 查询和 Command 对象创建和执行返回单个值的 SQL 语句。|  
|[如何：创建和执行不返回值的 SQL 语句](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)|详细介绍如何使用 TableAdapter 查询和 Command 对象创建和执行不返回任何值的 SQL 语句。|  
|[如何：执行返回行的存储过程](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)|详细介绍如何使用 TableAdapter 查询和 Command 对象执行返回行的存储过程。|  
|[如何：执行返回单个值的存储过程](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)|详细介绍如何使用 TableAdapter 查询和 Command 对象执行返回单个值的存储过程。|  
|[如何：执行不返回值的存储过程](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)|详细介绍如何使用 TableAdapter 查询和 Command 对象执行不返回任何值的存储过程。|  
|[如何：设置和获取命令对象的参数](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)|提供有关为查询和存储过程中的参数分配值，以及读取从执行的命令返回的参数值的详细信息。|  
|[演练：使用数据填充数据集](../Topic/Walkthrough:%20Filling%20a%20Dataset%20with%20Data.md)|提供创建数据集并使用数据库中的数据填充该数据集的详细信息。|  
|[演练：将 XML 数据读取到数据集](../data-tools/read-xml-data-into-a-dataset.md)|详细介绍一个 Windows 应用程序的创建过程，该应用程序将 XML 数据加载到数据集中，然后在 <xref:System.Windows.Forms.DataGridView> 控件中显示该数据集。|  
  
## 填充数据集  
 如果用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设计时工具（如[数据集设计器](../data-tools/creating-and-editing-typed-datasets.md)或[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)）创建数据集，则使用 TableAdapter 填充该数据集。  TableAdapter 执行 SQL 语句或存储过程。  
  
 如果不是使用设计时工具创建数据集，则必须使用数据适配器填充和更新数据。  （TableAdapter 不是 [.NET Framework 4.6 和 4.5](../Topic/.NET%20Framework%204.6%20and%204.5.md) 中的实际类，因此它们不适用于不是使用设计时工具创建的数据集。）  有关使用 TableAdapter 或数据适配器将数据加载到数据集的更多信息，请参见[如何：使用数据填充数据集](../data-tools/how-to-fill-a-dataset-with-data.md)。  
  
## TableAdapter 查询  
 可以执行 TableAdapter 查询以将数据填充到数据集中（更确切地说，是将数据加载到构成数据集的 DataTable 中）。  可以使用**“数据集设计器”**中的 [TableAdapter 查询配置向导](../data-tools/editing-tableadapters.md) 创建 TableAdapter 查询。  TableAdapter 查询显示为 TableAdapter 上的指定方法，并通过调用 TableAdapter 方法执行。  有关创建和执行 TableAdapter 查询的更多信息，请参见以下页：  
  
-   [如何：创建和执行返回行的 SQL 语句](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)  
  
-   [如何：创建和执行返回单个值的 SQL 语句](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)  
  
-   [如何：创建和执行不返回值的 SQL 语句](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)  
  
-   [如何：执行返回行的存储过程](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)  
  
-   [如何：执行返回单个值的存储过程](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)  
  
-   [如何：执行不返回值的存储过程](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)  
  
## Command 对象  
 使用命令对象可以直接对数据库执行 SQL 语句和存储过程，而不需要 <xref:System.Data.DataSet>、TableAdapter 或 <xref:System.Data.Common.DataAdapter>。  （术语“命令对象”是指您的应用程序正在使用的 .NET Framework 数据提供程序的特定命令。  例如，如果应用程序使用的是用于 SQL Server 的 .NET Framework 数据提供程序，则该命令对象为 <xref:System.Data.SqlClient.SqlCommand>。）  
  
 通过将数据命令的 `CommandType` 属性设置为 <xref:System.Data.IDbCommand.CommandType%2A> 枚举中的值之一，将命令配置为使用 SQL 语句或存储过程查询数据。  将 `CommandType` 设置为 <xref:System.Data.CommandType> 以便执行 SQL 语句，或将它设置为 <xref:System.Data.CommandType> 以便执行存储过程。  然后，将 `CommandText` 属性设置为 SQL 语句或存储过程的名称。  然后，通过调用数据命令的执行方法（`ExecuteReader`、`ExecuteScalar`、`ExecuteNonQuery`）之一执行该命令。  
  
 每个 [.NET Framework 数据提供程序](../Topic/.NET%20Framework%20Data%20Providers.md) 均提供一个为特定数据库进行了优化的命令对象。  
  
 使用数据命令，可在应用程序中进行以下操作：  
  
-   执行向您返回可以直接读取结果的“选择”\(Select\) 命令，而不是将结果加载到数据集内。  若要读取结果，请使用数据读取器（<xref:System.Data.OleDb.OleDbDataReader>、<xref:System.Data.SqlClient.SqlDataReader>、<xref:System.Data.Odbc.OdbcDataReader> 或 <xref:System.Data.OracleClient.OracleDataReader> 对象），其工作方式与可将控件绑定到的只读、只进游标类似。  这对于降低内存占用和非常快地加载只读数据的策略十分有用。  
  
-   执行数据库定义 \(DDL\) 命令以创建、编辑和移除表、存储过程及其他数据库结构。  （当然您必须有执行这些操作的权限。）  
  
-   执行命令以获取数据库目录信息。  
  
-   执行动态 SQL 命令以更新、插入或删除记录，而不是更新数据集表然后将更改复制到数据库。  
  
-   执行返回标量值（即单个值，如聚合函数 SUM、COUNT、AVG 等的结果）的命令。  
  
-   执行从 SQL Server 数据库（版本 7.0 或更高版本）返回 XML 格式的数据的命令。  典型的使用是执行一个查询并返回 XML 格式的数据，向其应用 XSLT 转换以将数据转换为 HTML，然后将结果发送给浏览器。  
  
 命令的属性包含对数据库执行命令所需的全部信息。  这包括：  
  
-   **一个连接** 命令引用一个连接，使用它与数据库通信。  
  
-   **命令的名称或文本** 命令包含 SQL 语句的实际文本或要执行的存储过程的名称。  
  
-   **参数** 命令可能要求您随命令传递参数值（输入参数）。  命令还可能以返回值或输出参数值的形式返回值。  每个命令都有一个参数集合，您可分别设置或读取这些参数以传递或接收值。  有关更多信息，请参见[如何：设置和获取命令对象的参数](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)。  
  
 您使用适于预期返回的结果的方法执行命令。  例如，您预期返回几行，则调用命令的 `ExecuteReader` 方法，这将记录返回到数据读取器。  如果您执行 UPDATE、INSERT 或 DELETE 命令，则调用命令的 `ExecuteNonQuery` 方法，这返回指示所影响的行数的值。  如果执行聚合函数（如返回客户的订单计数），则调用 `ExecuteScalar` 方法。  
  
### 多个结果集  
 命令对象的典型应用是返回单个数据表（一组行）。  但是，命令可以执行返回多个结果集的过程。  这可以不同方法实现。  一种方法是命令引用返回多个结果集的存储过程。  另一种方法是，命令可以包含两个（或多个）语句或存储过程名。  在该情况下，这些语句或存储过程按顺序运行，并且一次调用返回多个结果集。  
  
 如果为一个命令指定多个语句或过程，它们的类型必须相同。  例如，可以运行连续的 SQL 语句或连续的存储过程。  但是，不能在同一个命令中混合存储过程调用和 SQL 语句。  有关更多信息，请参见[使用 DataReader 检索数据](../Topic/Retrieving%20Data%20Using%20a%20DataReader.md)。  
  
> [!NOTE]
>  对于 Oracle，Oracle .NET Framework 数据提供程序不支持成批的 SQL 语句。  但是，它允许您使用多个 REF CURSOR 输出参数来填充一个数据集，每个参数都位于其各自的数据表中。  您必须定义这些参数，将它们标记为输出参数，并指出它们是 REF CURSOR 数据类型。  注意，因为当执行 SQL 语句时，Oracle 不提供确定表名和列名所必需的信息，所以，当从 REF CURSOR 参数将 <xref:System.Data.OracleClient.OracleDataAdapter> 对象填充到存储过程时，您将无法使用 `Update` 方法。  
  
## 安全性  
 在使用将 `CommandType` 属性设置为 <xref:System.Data.CommandType> 的数据命令时，将从客户端发送的信息传递到数据库前请仔细检查该信息。  恶意用户可能会尝试发送（插入）修改过的或其他 SQL 语句，以获得未经授权的访问或破坏数据库。  在将用户输入内容传输到数据库之前，应始终确认这些信息是有效的。  如果可能的话，请始终使用参数化查询或存储过程，这是最佳做法。  
  
## 请参阅  
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)   
 [Visual Studio 中用于处理数据源的工具](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)