---
title: "如何：使用 TableAdapter 更新数据 | Microsoft Docs"
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
  - "数据 [Visual Studio], TableAdapter"
  - "数据 [Visual Studio], 更新"
  - "保存数据"
  - "TableAdapter, 更新数据"
  - "更新数据, TableAdapter"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 TableAdapter 更新数据
在修改并验证了数据集中的数据后，可能需要将更新后的数据发回数据库。  要将修改后的数据发送到数据库，需要调用 [TableAdapter](../data-tools/tableadapter-overview.md) 的 `Update` 方法。  此适配器的 `Update` 方法将更新单个数据表并根据该表中每个数据行的 <xref:System.Data.DataRow.RowState%2A> 执行正确的命令（INSERT、UPDATE 或 DELETE）。  当您将数据保存在相关表中时，Visual Studio 提供的 TableAdapterManager 组件有助于根据在数据库中定义的外键约束以正确的顺序执行保存。  有关更多信息，请参见[分层更新概述](../Topic/Hierarchical%20Update%20Overview.md)。  
  
> [!NOTE]
>  由于尝试使用数据集的内容更新数据源可能会导致错误，因此应将调用该适配器的 `Update` 方法的代码放入 `try`\/`catch` 块内。  
  
 根据不同的业务需求，更新数据源的确切过程可能会有所不同，但是您的应用程序应该包括以下步骤：  
  
1.  在 `try`\/`catch` 块中调用适配器的 `Update` 方法。  
  
2.  如果捕获到异常，则找到引发错误的数据行。  有关更多信息，请参见[如何：定位出错的行](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md)。  
  
3.  解决数据行中的问题（在可能的情况下以编程方式进行，或者将无效的行提供给用户进行修改），然后重新尝试更新（<xref:System.Data.DataRow.HasErrors%2A>、<xref:System.Data.DataTable.GetErrors%2A>）。  
  
## 将数据保存到数据库  
 调用 TableAdapter 的 `Update` 方法，传递数据表的名称，该数据表包含要写入数据库的值。  
  
#### 使用 TableAdapter 更新具有数据集的数据库  
  
-   在 `try`\/`catch` 块中包含适配器的 `Update` 方法。  下面的示例演示如何尝试用 `NorthwindDataSet` 中的 `Customers` 表的内容从 `try`\/`catch` 块内部执行更新。  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## 使用 TableAdapter 更新数据集中的两个相关表  
 更新数据集中的相关表时，为了减小违反引用完整性约束的可能性，必须以正确的顺序进行更新。  命令执行的顺序也将遵循数据集中 <xref:System.Data.DataRowCollection> 的索引的顺序。  为了防止引发数据完整性错误，最佳做法是按照下面的顺序更新数据库：  
  
1.  子表：删除记录。  
  
2.  父表：插入、更新和删除记录。  
  
3.  子表：插入和更新记录。  
  
    > [!NOTE]
    >  如果要更新两个或更多相关表，应将所有更新逻辑包括在一个事务内。  事务是指一个过程，它在提交任何更改之前都先要确保对数据库的所有相关更改均可成功完成。  有关更多信息，请参见 [事务和并发](../Topic/Transactions%20and%20Concurrency.md)。  
  
#### 使用 TableAdapter 更新两个相关表  
  
1.  创建三个临时数据表以保存不同的记录。  
  
2.  从 `try`\/`catch` 块中为每个子行集调用 `Update` 方法。  如果发生更新错误，则应分支出来并解决这些错误。  
  
3.  将更改提交到数据库。  
  
4.  处置临时数据表以释放资源。  
  
     下面的示例显示如何用包含相关表的数据集更新数据源。  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_2.cs)]  
  
## 请参阅  
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)