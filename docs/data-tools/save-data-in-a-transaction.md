---
title: "演练： 将数据保存在事务中 |Microsoft 文档"
ms.custom: 
ms.date: 09/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f8d1d25c2aaa66658df53dbaea366c196e8e7f6b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-save-data-in-a-transaction"></a>演练： 将数据保存在事务中
本演练演示如何使用在事务中保存数据<xref:System.Transactions>命名空间。 在本演练将创建一个 Windows 窗体应用程序。 将使用数据源配置向导在 Northwind 示例数据库中创建两个表的数据集。 你将添加数据控件绑定到 Windows 窗体，并将修改 BindingNavigator 的保存按钮以更新在 TransactionScope 内的数据库的代码。  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**.NET 桌面开发**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
## <a name="create-a-windows-forms-application"></a>创建 Windows 窗体应用程序  
 第一步是创建**Windows 窗体应用程序**。  
  
#### <a name="to-create-the-new-windows-project"></a>创建新的 Windows 项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**命名为 SavingDataInATransactionWalkthrough**，然后选择**确定**。 
  
     **命名为 SavingDataInATransactionWalkthrough**创建项目并将其添加到**解决方案资源管理器**。  
  
## <a name="create-a-database-data-source"></a>创建数据库数据源  
 此步骤使用**数据源配置向导**创建数据源基于`Customers`和`Orders`Northwind 示例数据库中的表。  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  上**数据**菜单上，选择**显示数据源**。  
  
2.  在**数据源**窗口中，选择**添加新数据源**启动**数据源配置向导**。  
  
3.  上**选择数据源类型**屏幕上，选择**数据库**，然后选择**下一步**。  
  
4.  上**选择你的数据连接**屏幕执行下列操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         - 或 -  
  
    -   选择**新连接**以启动**添加/修改连接**对话框框中，并创建到 Northwind 数据库的连接。  
  
5.  如果你的数据库需要密码，选择该选项以包括敏感数据，然后选择**下一步**。  
  
6.  上**将连接字符串保存到应用程序配置文件**屏幕上，选择**下一步**。  
  
7.  上**选择数据库对象**屏幕中，展开**表**节点。  
  
8.  选择`Customers`和`Orders`表，，然后选择**完成**。  
  
     **NorthwindDataSet**添加到你的项目和`Customers`和`Orders`表将显示在**数据源**窗口。  
  
## <a name="add-controls-to-the-form"></a>将控件添加到窗体  
 你可以通过将某些项从创建数据绑定控件**数据源**拖动到窗体的窗口。  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>若要创建数据绑定 Windows 窗体上控件  
  
-   在**数据源**窗口中，展开**客户**节点。  
  
-   将主**客户**节点从**数据源**窗口拖到**Form1**。  
  
     用于导航记录的 <xref:System.Windows.Forms.DataGridView> 控件和工具栏（<xref:System.Windows.Forms.BindingNavigator>）将显示在窗体上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， `CustomersTableAdapter`， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。  
  
-   将相关**订单**节点 (非主**订单**节点，但下面的相关的子表节点**传真**列) 拖到窗体下面**CustomersDataGridView**。  
  
     窗体上显示一个 <xref:System.Windows.Forms.DataGridView>。 `OrdersTableAdapter`和<xref:System.Windows.Forms.BindingSource>组件栏中出现。  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>添加对 System.Transactions 程序集的引用  
 事务使用 <xref:System.Transactions> 命名空间。 默认情况下，没有添加对 system.transactions 程序集的项目引用，因此你需要手动将其添加。  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>添加对 System.Transactions DLL 文件的引用  
  
1.  上**项目**菜单上，选择**添加引用**。  
  
2.  选择**System.Transactions** (上**.NET**选项卡)，然后选择**确定**。  
  
     对引用**System.Transactions**添加到项目。  
  
## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>修改 BindingNavigator 的 SaveItem 按钮中的代码  
 拖放到窗体的第一个表，代码添加到默认情况下`click`事件保存按钮上<xref:System.Windows.Forms.BindingNavigator>。 你需要手动添加代码以更新所有附加的表。 对于本演练中，我们将重构的现有保存代码源自保存按钮的 click 事件处理程序。 我们还会创建更多的方法，以提供基于是否需要行添加或删除特定的更新功能。  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>修改自动生成的保存代码  
  
1.  选择**保存**按钮上**customersbindingnavigator** （带有软盘图标的按钮）。  
  
2.  将 `CustomersBindingNavigatorSaveItem_Click` 方法替换为以下代码：  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
对相关数据的协调更改的顺序如下：  
  
-   删除子记录。 (在这种情况下，删除从记录`Orders`表。)  
  
-   删除父记录。 (在这种情况下，删除从记录`Customers`表。)  
  
-   插入父记录。 (在这种情况下，插入中的记录`Customers`表。)  
  
-   插入子记录。 (在这种情况下，插入中的记录`Orders`表。)  
  
#### <a name="to-delete-existing-orders"></a>删除现有顺序  
  
-   添加以下`DeleteOrders`方法**Form1**:  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### <a name="to-delete-existing-customers"></a>删除现有客户  
  
-   添加以下`DeleteCustomers`方法**Form1**:  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### <a name="to-add-new-customers"></a>添加新客户  
  
-   添加以下`AddNewCustomers`方法**Form1**:  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### <a name="to-add-new-orders"></a>添加新顺序  
  
-   添加以下`AddNewOrders`方法**Form1**:  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## <a name="run-the-application"></a>运行此应用程序  
  
#### <a name="to-run-the-application"></a>要运行应用程序  
  
-   选择**F5**运行该应用程序。  
  
## <a name="see-also"></a>请参阅
[如何： 使用事务保存数据](../data-tools/save-data-by-using-a-transaction.md)  
[将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)