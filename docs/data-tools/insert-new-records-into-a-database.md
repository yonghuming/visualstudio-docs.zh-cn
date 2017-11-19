---
title: "将新记录插入数据库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2450ed950227b6755b57f20f3520a1e75034aafe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="insert-new-records-into-a-database"></a>将新记录插入数据库
若要将新记录插入数据库，可以使用`TableAdapter.Update`方法，或 TableAdapter 的 DBDirect 方法之一 (具体而言`TableAdapter.Insert`方法)。 有关详细信息，请参阅[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 如果你的应用程序不使用 Tableadapter，则可以使用命令对象 (例如， <xref:System.Data.SqlClient.SqlCommand>) 在你的数据库中插入新记录。
  
 如果你的应用程序使用数据集来存储数据，使用`TableAdapter.Update`方法。 `Update`方法可发送到数据库 （更新、 插入和删除） 的所有更改。  
  
 如果你的应用程序将使用对象来存储数据，或如果你想在数据库中，创建新记录的更好地控制使用`TableAdapter.Insert`方法。  
  
 如果你 TableAdapter 不具有`Insert`方法，这意味着任一 TableAdapter 配置为使用存储的过程或其`GenerateDBDirectMethods`属性设置为`false`。 尝试设置 TableAdapter 的`GenerateDBDirectMethods`属性`true`中**数据集设计器**，然后将保存数据集。 这将再生成 TableAdapter。 如果仍不具有 TableAdapter`Insert`方法，则表可能不会提供足够的架构信息来区分各个行 （例如，可能有表上的没有主密钥集）。  
  
## <a name="insert-new-records-by-using-tableadapters"></a>使用 Tableadapter 插入新记录  
 Tableadapter 提供不同的方式将新记录插入数据库，具体取决于你的应用程序的要求。  
  
 如果你的应用程序使用数据集来存储数据，则你可以只需将新记录添加到所需<xref:System.Data.DataTable>在数据集，然后再调用`TableAdapter.Update`方法。 `TableAdapter.Update`方法发送的任何更改<xref:System.Data.DataTable>到数据库 （包括修改和删除记录）。  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>若要将新记录插入数据库使用 TableAdapter.Update 方法  
  
1.  将新记录添加到所需<xref:System.Data.DataTable>通过创建新<xref:System.Data.DataRow>和将其添加到<xref:System.Data.DataTable.Rows%2A>集合。 
  
2.  新行添加到后<xref:System.Data.DataTable>，调用`TableAdapter.Update`方法。 你可以控制要通过传入整个更新的数据量<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>，数组<xref:System.Data.DataRow>s 或单个<xref:System.Data.DataRow>。  
  
 下面的代码演示如何添加到新的记录<xref:System.Data.DataTable>，然后调用`TableAdapter.Update`方法以将新行保存到数据库。 (此示例使用`Region`Northwind 数据库中的表。)  
  
 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>若要将新记录插入数据库使用 TableAdapter.Insert 方法  
如果你的应用程序使用对象来存储数据，你可以使用`TableAdapter.Insert`方法直接在数据库中创建新行。 `Insert`方法接受每个列作为参数的单个值。 调用方法将一条新记录插入数据库中传递的参数值。  
  
- 调用 TableAdapter 的`Insert`方法，在值中为每一列将作为参数传递。  

 以下过程演示如何使用`TableAdapter.Insert`方法插入行。 此示例将数据插入`Region`Northwind 数据库中的表。  
  
 > [!NOTE]
 >  如果你没有可用的实例，实例化你想要使用的 TableAdapter。  
  
 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>使用命令对象插入新记录  
你可以直接在使用命令对象的数据库中插入新记录。    
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>若要将新记录插入数据库通过使用命令对象  
  
-   创建新的命令对象，并将其`Connection`， `CommandType`，和`CommandText`属性。  

 下面的示例演示插入记录到使用命令对象的数据库。 它将数据插入`Region`Northwind 数据库中的表。
  
 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 你必须有权尝试连接到数据库以及执行插入到所需的表的权限。  
  
## <a name="see-also"></a>另请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)