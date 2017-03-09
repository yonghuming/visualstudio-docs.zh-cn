---
title: "如何：使用数据填充数据集 | Microsoft Docs"
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
  - "数据 [Visual Basic], 加载到数据集中"
  - "数据集 [Visual Basic], 填充"
  - "DataTable 对象, 加载"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：使用数据填充数据集
短语“用数据填充数据集”指的是将数据加载到组成数据集的各个 <xref:System.Data.DataTable> 对象中。  可以通过执行 TableAdapter 查询或数据适配器（例如 <xref:System.Data.SqlClient.SqlDataAdapter>）命令来填充数据表。  
  
 使用 TableAdapter 还是使用数据适配器取决于数据集的创建方式。  如果使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的设计工具（例如[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)），则数据集将包含 TableAdapter。  有关 TableAdapter 的更多信息，请参见 [TableAdapter 概述](../data-tools/tableadapter-overview.md)。  如果以编程方式创建数据集，则通常需要创建数据适配器以将数据加载到数据表中。  
  
> [!NOTE]
>  将项从 [“数据源”窗口](../Topic/Data%20Sources%20Window.md) 拖动到窗体上时，用数据填充数据表的代码会自动添加到 `Form_Load` 事件处理程序。  在代码编辑器中打开窗体以查看用于填充指定表的具体语法。  如果窗体加载时不希望填充表，则可将此代码移动到其他的方法中，或将其完全移除。  
  
## 使用 TableAdapter 填充数据集  
 调用 TableAdapter 上的某个查询将数据加载到数据集中的数据表。  将要填充的 <xref:System.Data.DataTable> 传递给 TableAdapter 查询。  如果查询带有参数，则还要将这些参数传递到该方法。  如果数据集包含多个表，则应为每个表提供不同的 TableAdapter，而且必须分别填充每个表。  
  
> [!NOTE]
>  默认情况下，每次执行 TableAdapter 查询时，在将查询结果加载到表中之前首先会清除表中的数据。  可以通过将 TableAdapter 的 `ClearBeforeFill` 属性设置为 `false` 来保留表中的现有数据并追加查询结果。  
  
#### 使用 TableAdapter 利用数据填充数据集  
  
1.  在**“代码编辑器”**中打开窗体或组件。  
  
2.  将代码添加到应用程序中需要在此用数据加载数据表的任何位置。  如果查询不包含参数，则传入要填充的 <xref:System.Data.DataTable>。  代码应类似于如下所示：  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  如果查询包含参数，则传入要填充的 <xref:System.Data.DataTable> 及查询所需的参数。  根据查询中的实际参数，代码将类似于以下示例：  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## 使用 DataAdapter 填充数据集  
 调用数据适配器的 `Fill` 方法。  这会导致适配器执行在其 `SelectCommand` 属性中所引用的 SQL 语句或存储过程，然后将结果放入数据集中的表中。  如果数据集包含多个表，则应该为每个表提供不同的数据适配器，而且必须单独填充每个表。  
  
#### 使用 DataAdapter 利用数据填充数据集  
  
-   调用 <xref:System.Data.Common.DataAdapter> 的 <xref:System.Data.Common.DataAdapter.Fill%2A> 方法，并传入将要在其中加载数据的 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable>。  例如：  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     通常应提供将要在其中加载数据的 <xref:System.Data.DataTable> 的名称。  如果传入的是 <xref:System.Data.DataSet> 的名称，而不是某个具体数据表的名称，则名为 `Table1` 的 <xref:System.Data.DataTable> 将被添加到数据集并被加载来自数据库的结果（而不是在数据集中的现有 <xref:System.Data.DataTable> 中加载数据）。  有关更多信息，请参见[从 DataAdapter 填充 DataSet](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)。  
  
## 请参阅  
 [用数据填充数据集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)