---
title: "使用 TableAdapter 更新数据 |Microsoft 文档"
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
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 7d49f0ddc965327334aea471b1276b4e78987ec2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="update-data-by-using-a-tableadapter"></a>使用 TableAdapter 更新数据
在修改数据集中的数据并将其验证后，你可以更新将数据发送回数据库通过调用`Update`方法[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。 `Update`方法更新单个数据表并运行的命令正确无误 （INSERT、 UPDATE 或 DELETE） 基于<xref:System.Data.DataRow.RowState%2A>的表中每个数据行。 当数据集有相关的表时，Visual Studio 将生成用于执行更新操作的 TableAdapterManager 类。 TableAdapterManager 类可确保按正确的顺序基于数据库中定义的外键约束进行更新。 当你使用数据绑定控件时，数据绑定体系结构将创建名为 tableAdapterManager TableAdapterManager 类的成员变量。 
  
> [!NOTE]
>  当你尝试更新数据源的数据集的内容时，你会遇到错误。若要避免错误，我们建议你将代码调用该适配器放`Update`中的方法`try` / `catch`块。  
  
 用于更新数据源的确切过程根据业务需求，可能会有所不同，但是包括以下步骤：  
  
1.  调用该适配器`Update`中的方法`try` / `catch`块。  
  
2.  如果捕获了一个异常，将查找导致错误的数据行。 
  
3.  对帐中数据的问题行 （你可以如果以编程方式或无效的行显示给用户进行修改），然后再试一次更新 (<xref:System.Data.DataRow.HasErrors%2A>， <xref:System.Data.DataTable.GetErrors%2A>)。  
  
## <a name="save-data-to-a-database"></a>将数据保存到数据库  
 调用`Update`的 TableAdapter 方法。 传递的包含要写入到数据库的值的数据表的名称。  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>通过使用 TableAdapter 更新数据库  
  
-   括起 TableAdapter 的`Update`中的方法`try` / `catch`块。 下面的示例演示如何更新的内容`Customers`表中`NorthwindDataSet`中`try` / `catch`块。  
  
     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)