---
title: "如何：将数据从对象保存到数据库 | Microsoft Docs"
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
  - "数据访问 [Visual Studio], 对象"
  - "保存数据"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将数据从对象保存到数据库
通过将对象中的值传递到 TableAdapter 的 DBDirect 方法之一（例如，`TableAdapter.Insert`），可将对象中的数据保存到数据库中。  有关更多信息，请参见 [TableAdapter 概述](../data-tools/tableadapter-overview.md)。  
  
 若要保存对象集合中的数据，请循环通过对象集合（例如，for\-next 循环），然后使用 TableAdapter 的 DBDirect 方法之一将每个对象的值发送到数据库中。  
  
 默认情况下，DBDirect 方法在 TableAdapter 上创建，能够直接对数据库执行操作。  这些方法可以直接调用，它们不要求 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 对象来协调更改即可将更新发送到数据库。  
  
> [!NOTE]
>  配置 TableAdapter 时，主查询必须提供足够的信息，才能创建 DBDirect 方法。  例如，如果将 TableAdapter 配置为从未定义主键列的表中查询数据，它将不会生成 DBDirect 方法。  
  
|TableAdapter DBDirect 方法|说明|  
|------------------------------|--------|  
|`TableAdapter.Insert`|向数据库中添加新记录，此方法允许将值作为方法参数传入各个列。|  
|`TableAdapter.Update`|更新数据库中的现有记录。  `Update` 方法将原始列值和新列值用作方法参数。  原始值用于定位原始记录，新值用于更新该记录。<br /><br /> 通过将 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow>、或 <xref:System.Data.DataRow> 数组用作方法参数，`TableAdapter.Update` 方法还可用于将数据集中的更改协调回数据库。|  
|`TableAdapter.Delete`|在基于作为方法参数传入的原始列值的数据库中，删除其现有记录。|  
  
### 将对象中的新记录保存到数据库中  
  
-   通过将值传递给 `TableAdapter.Insert` 方法可创建这些记录。  
  
     下面的示例通过将 `currentCustomer` 对象中的值传递给 `TableAdapter.Insert` 方法，在 `Customers` 表中创建一项新的客户记录。  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### 将对象中的现有记录更新到数据库  
  
-   修改记录：调用 `TableAdapter.Update` 方法并传入新值可更新记录，而传入原始值可定位记录。  
  
    > [!NOTE]
    >  对象需要保留其原始值，才能将它们传递给 `Update` 方法。  此示例使用前缀为 `orig` 的属性存储原始值。  
  
     下面的示例通过将 `Customer` 对象中的新值和原始值传递给 `TableAdapter.Update` 方法，更新 `Customers` 表中的现有记录。  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### 删除数据库中的现有记录  
  
-   通过调用 `TableAdapter.Delete` 方法并传入原始值定位记录，可删除记录。  
  
    > [!NOTE]
    >  对象需要保留其原始值，才能将它们传递给 `Delete` 方法。  此示例使用前缀为 `orig` 的属性存储原始值。  
  
     下面的示例通过将 `Customer` 对象中的原始值传递给 `TableAdapter.Delete` 方法，删除 `Customers` 表中的记录。  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## .NET Framework 安全性  
 您必须具有相应的权限，才能对数据库中的表执行选定的 INSERT、UPDATE 或 DELETE。  
  
## 请参阅  
 [Visual Studio 中的对象绑定](../data-tools/bind-objects-in-visual-studio.md)   
 [如何：连接到对象中的数据](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [演练：连接到对象中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [如何：使用 TableAdapter 直接访问数据库](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)