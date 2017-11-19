---
title: "将数据从对象保存到数据库 |Microsoft 文档"
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 1c7e99ce49df969fae439afac5d65369fae9c37a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="save-data-from-an-object-to-a-database"></a>将数据从对象保存到数据库
你可以通过将值从你的对象传递到 TableAdapter 的 DBDirect 方法之一将数据保存到数据库的对象中 (例如， `TableAdapter.Insert`)。 有关详细信息，请参阅[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 若要保存的对象的集合中的数据，循环访问集合的对象 （例如，为下一步循环），并使用 TableAdapter 的 DBDirect 方法之一将每个对象的值发送到数据库。  
  
 默认情况下，可以直接对数据库运行的 TableAdapter 上创建 DBDirect 方法。 这些方法可以直接调用，而不需要<xref:System.Data.DataSet>或<xref:System.Data.DataTable>对象来协调更改即可将更新发送到数据库。  
  
> [!NOTE]
>  在配置 TableAdapter 时，主查询必须提供足够的信息供要创建的 DBDirect 方法。 例如，如果 TableAdapter 配置查询数据的表中没有定义主键列，它不生成 DBDirect 方法。  
  
|TableAdapter DBDirect 方法|描述|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|向数据库添加新记录，并使您能够在单个列作为方法参数的值传递。|  
|`TableAdapter.Update`|更新现有数据库中的记录。 `Update`方法采用原始列值和新列作为方法参数的值。 原始值中用于查找原始记录，并使用新值来更新该记录。<br /><br /> `TableAdapter.Update`方法还可用于协调数据集中的更改回数据库采用<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或数组<xref:System.Data.DataRow>的方法参数。|  
|`TableAdapter.Delete`|删除现有记录从基于作为方法参数中传递的原始列值的数据库。|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>若要将新记录从对象保存到数据库  
  
-   将值传递给创建记录`TableAdapter.Insert`方法。  
  
     下面的示例创建中的新客户记录`Customers`表中的值传递`currentCustomer`对象传递给`TableAdapter.Insert`方法。  
  
     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>若要更新现有记录从对象到数据库  
  
-   通过调用修改记录`TableAdapter.Update`方法，传入新值更新的记录，并传入要定位该记录的原始值。  
  
    > [!NOTE]
    >  你的对象需要维护原始值，以便将它们传递给`Update`方法。 此示例使用具有属性`orig`前缀来存储的原始值。  
  
     下面的示例更新中的现有记录`Customers`表中的新的和原始值传递`Customer`对象传递给`TableAdapter.Update`方法。  
  
     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>若要从数据库中删除现有记录  
  
-   通过调用中删除记录`TableAdapter.Delete`方法并传入要定位该记录的原始值。  
  
    > [!NOTE]
    >  你的对象需要维护原始值，以便将它们传递给`Delete`方法。 此示例使用具有属性`orig`前缀来存储的原始值。  
  
     下面的示例删除的记录从`Customers`通过传递中的原始值的表`Customer`对象传递给`TableAdapter.Delete`方法。  
  
     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您必须有权执行所选的 INSERT、 UPDATE 或 DELETE 中数据库的表。  
  
## <a name="see-also"></a>另请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)