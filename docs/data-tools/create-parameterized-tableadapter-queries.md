---
title: "创建参数化的 TableAdapter 查询 |Microsoft 文档"
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
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6b80f370f670f4dff4b65d7c0e7658f855d5e573
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="create-parameterized-tableadapter-queries"></a>创建参数化的 TableAdapter 查询
参数化查询将返回满足查询内的 WHERE 子句条件的数据。 例如，通过在返回客户列表的 SQL 语句的末尾添加 `WHERE City = @City`，可以参数化客户列表，使之只显示某个城市的客户。  
  
 创建中的参数化的 TableAdapter 查询**数据集设计器**。你还可以使用 Windows 应用程序中创建它们**参数化数据源**命令**数据**菜单。 **参数化数据源**命令将创建可以在此输入参数值，并运行查询的窗体上的控件。  
  
> [!NOTE]
>  当构造参数化的查询，使用特定于您要针对用于编码的数据库的参数表示法。 例如，Access 和 OleDb 数据源使用问号“?”表示参数，所以 WHERE 子句将类似于：`WHERE City = ?`。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与中的描述的帮助，具体取决于你现用的设置或要使用的版本不同。 若要更改设置，请转到**工具**菜单，然后选择**导入和导出设置**。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="create-a-parameterized-tableadapter-query"></a>创建参数化的 TableAdapter 查询  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>在“数据集设计器”中创建参数化查询  
  
-   将 WHERE 子句和所需参数添加到 SQL 语句中，以创建新的 TableAdapter。 有关详细信息，请参阅[创建和配置 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
     - 或 -  
  
-   将 WHERE 子句和所需参数添加到 SQL 语句中，以向现有 TableAdapter 中添加查询。
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>在设计数据绑定窗体时创建参数化查询  
  
1.  在窗体中选择已绑定到数据集的控件。 有关详细信息，请参阅[绑定 Windows 窗体控件添加到 Visual Studio 中的数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
2.  上**数据**菜单上，选择**添加查询**。  
  
3.  完成**搜索标准生成器**对话框中，将 WHERE 子句和所需参数添加到 SQL 语句。  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>将查询添加到现有数据绑定窗体  
  
1.  打开的窗体中**Windows 窗体设计器**。  
  
2.  上**数据**菜单上，选择**添加查询**或**数据智能标记**。  
  
    > [!NOTE]
    >  如果**添加查询**上不可用**数据**菜单中，选择要添加到参数化功能，显示的数据源你窗体上控件。 例如，如果窗体在 <xref:System.Windows.Forms.DataGridView> 控件中显示数据，则选择该控件。 如果窗体在各个控件中显示数据，则选择任意数据绑定控件。  
  
3.  在**选择数据源表**区域中，选择你希望表添加到参数化功能。  
  
4.  中键入一个名称**新查询名称**框中，如果要创建新查询。  
  
     - 或 -  
  
     选择一个查询中的**现有查询名称**框。  
  
5.  在**查询文本**框中，键入查询采用参数。  
  
6.  选择“确定”。  
  
     一个控件，用于输入参数的和一**负载**按钮添加到窗体中<xref:System.Windows.Forms.ToolStrip>控件。  
  
#### <a name="querying-for-null-values"></a>查询的 null 值  
TableAdapter 参数你想要查询没有当前值的记录可以分配 null 值。 例如，考虑下面的查询具有`ShippedDate`参数在其`WHERE`子句：  
  
 ```sql
SELECT CustomerID, OrderDate, ShippedDate  
FROM Orders  
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```  
  
 如果这是 TableAdapter 的查询，你无法查询未装运替换为以下代码的所有订单：  
  
 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]  

 若要启用要接受 null 值的查询：

1.  在**数据集设计器**，选择需要接受 null 参数值的 TableAdapter 查询。  
  
2.  在**属性**窗口中，选择**参数**，然后单击省略号 (**...**) 按钮以打开**参数集合编辑器**。  
  
3.  选择允许 null 值的参数并设置**AllowDbNull**属性`true`。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Tableadapter 填充数据集](../data-tools/fill-datasets-by-using-tableadapters.md)