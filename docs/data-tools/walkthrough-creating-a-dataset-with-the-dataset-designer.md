---
title: "演练： 创建数据集与数据集设计器 |Microsoft 文档"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: f327d2010105c12c4b137317ed2406cae6cad9a3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>演练：使用数据集设计器创建数据集
在本演练将创建数据集使用**数据集设计器**。 它将指导您完成创建新的项目并添加一个新的过程**数据集**到它的项。 你将学习如何创建基于不使用向导的数据库的表中的表。  
  
 本演练涉及以下任务：  
  
-   创建一个新**Windows 窗体应用程序**项目。  
  
-   添加一个空**数据集**到项目的项。  
  
-   创建和配置应用程序中的数据源，通过构建具有的数据集**数据集设计器**。  
  
-   创建到 Northwind 数据库中的连接**服务器资源管理器**。  
  
-   使用 Tableadapter 创建表，在基于数据库中的表的数据集。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**数据存储和处理**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
## <a name="creating-a-new-windows-forms-application-project"></a>创建新的 Windows 窗体应用程序项目  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>若要创建新的 Windows 窗体应用程序项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**DatasetDesignerWalkthrough**，然后选择**确定**。  
  
     Visual Studio 将添加到项目**解决方案资源管理器**和设计器中显示的新窗体。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>将新的数据集添加到应用程序  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>若要向项目添加新的数据集项  
  
1.  上**项目**菜单上，选择**添加新项...**.  
  
     “添加新项”对话框随即出现。  
  
2.  在左侧窗格中，选择**数据**，然后选择**数据集**在中间窗格中。  
  
3.  命名数据集**NorthwindDataset**，然后选择**添加**。  
  
     Visual Studio 将添加名为的文件**NorthwindDataset.xsd**到项目并将其在打开**数据集设计器**。  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>在服务器资源管理器中创建的数据连接  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>若要创建到 Northwind 数据库的连接  
  
1.  上**视图**菜单上，单击**服务器资源管理器**。  
  
2.  在**服务器资源管理器**，单击**连接到数据库**按钮。  
  
3.  创建到 Northwind 示例数据库的连接。  
  
## <a name="creating-the-tables-in-the-dataset"></a>在数据集中创建表  
本部分介绍如何将表添加到数据集。  
  
#### <a name="to-create-the-customers-table"></a>创建 Customers 表  
  
1.  展开中创建的数据连接**服务器资源管理器**，然后展开**表**节点。  
  
2.  拖动**客户**表从**服务器资源管理器**到**数据集设计器**。  
  
     A**客户**数据表和**CustomersTableAdapter**添加到数据集。  
  
#### <a name="to-create-the-orders-table"></a>创建 Orders 表  
  
-   拖动**订单**表从**服务器资源管理器**到**数据集设计器**。  
  
     **订单**数据表**OrdersTableAdapter**，和之间的数据关系**客户**和**订单**表将添加到数据集。  
  
#### <a name="to-create-the-orderdetails-table"></a>若要创建 OrderDetails 表  
  
-   拖动**订单详细信息**表从**服务器资源管理器**到**数据集设计器**。  
  
     **订单详细信息**数据表**OrderDetailsTableAdapter**，和之间的数据关系**订单**和**OrderDetails**表将添加到数据集。  
  
## <a name="next-steps"></a>后续步骤  
  
### <a name="to-add-functionality-to-your-application"></a>将功能添加到你的应用程序  
  
-   保存的数据集。  
  
-   中选择项目**数据源**窗口并将它们拖到窗体。 有关详细信息，请参阅[绑定 Windows 窗体控件添加到 Visual Studio 中的数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
-   将多个查询添加到 Tableadapter。 
  
-   添加到的验证逻辑<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>的数据集中数据表的事件。 有关详细信息，请参阅[验证数据集中的数据](../data-tools/validate-data-in-datasets.md)。  
  
## <a name="see-also"></a>请参阅
[在 Visual Studio 中创建和配置数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[验证数据](../data-tools/validate-data-in-datasets.md)   
[保存数据](../data-tools/saving-data.md)