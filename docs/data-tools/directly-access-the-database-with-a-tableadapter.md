---
title: "如何：使用 TableAdapter 直接访问数据库 | Microsoft Docs"
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
  - "数据 [Visual Studio], 保存"
  - "数据库 [Visual Basic], 使用 TableAdapter 访问"
  - "数据集 [Visual Basic], 添加到项目"
  - "DBDirect 方法"
  - "GenerateDbDirectMethods 属性"
  - "保存数据"
  - "TableAdapter.Delete 方法"
  - "TableAdapter.GenerateDBDirectMethods 属性"
  - "TableAdapter.Insert 方法"
  - "TableAdapter.Update 方法"
  - "TableAdapter"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 TableAdapter 直接访问数据库
除了 `InsertCommand`、`UpdateCommand` 和 `DeleteCommand` 之外，创建 TableAdapter 时还生成了一些可以直接在数据库上执行的方法。  可以直接调用这些方法（`TableAdapter.Insert`、`TableAdapter.Update` 和 `TableAdapter.Delete`）对数据库中的数据进行操作。  
  
 如果不想创建这些直接方法，可在**“属性”**窗口中将 TableAdapter 的 `GenerateDbDirectMethods` 属性设置为 `false`。  除了 TableAdapter 的主查询之外，所有添加到 TableAdapter 的查询也是独立查询 \-\- 它们不生成这些 DbDirect 方法。  
  
## 直接向数据库发送命令  
 调用执行您尝试完成的任务的 TableAdapter DbDirect 方法。  
  
#### 直接向数据库中插入新记录  
  
-   调用 TableAdapter 的 `Insert` 方法，为每一列传入值作为参数。  以下过程使用 Northwind 数据库的 `Region` 表作为示例。  
  
    > [!NOTE]
    >  如果没有实例可用，请实例化您要使用的 TableAdapter。  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### 直接在数据库中更新记录  
  
-   调用 TableAdapter 的 `Update` 方法，以参数的形式为每一列传入新值和原始值。  
  
    > [!NOTE]
    >  如果没有实例可用，请实例化您要使用的 TableAdapter。  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### 直接从数据库中删除记录  
  
-   调用 TableAdapter 的 `Delete` 方法，为每一列传入值作为 `Delete` 方法的参数  （此示例使用 Northwind 数据库的 `Region` 表）。  
  
    > [!NOTE]
    >  如果没有实例可用，请实例化您要使用的 TableAdapter。  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## 请参阅  
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)   
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [命令和参数](../Topic/Commands%20and%20Parameters.md)