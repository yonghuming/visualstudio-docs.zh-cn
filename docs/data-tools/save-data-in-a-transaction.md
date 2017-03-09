---
title: "演练：在事务中保存数据 | Microsoft Docs"
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
  - "数据 [Visual Studio], 保存在事务中"
  - "保存数据"
  - "System.Transactions 命名空间"
  - "Transactions 命名空间"
  - "事务, 保存数据"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：在事务中保存数据
本演练演示如何使用 <xref:System.Transactions> 命名空间在事务中保存数据。  此示例使用源自 Northwind 示例数据库的 `Customers` 和 `Orders` 表。  
  
## 系统必备  
 本演练需要对 Northwind 示例数据库的访问权限。  有关设置 Northwind 示例数据库的信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建 Windows 应用程序  
 第一步是创建**“Windows 应用程序”**。  
  
#### 创建新的 Windows 项目  
  
1.  在 Visual Studio 中，从**“文件”**菜单创建一个新的**“项目”**。  
  
2.  将项目命名为 SavingDataInATransactionWalkthrough。  
  
3.  选择**“Windows 应用程序”**，然后单击**“确定”**。  有关详细信息，请参阅[客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     **“SavingDataInATransactionWalkthrough”**项目即被创建并添加到**“解决方案资源管理器”**中。  
  
## 创建数据库数据源  
 此步骤使用 [数据源配置向导](../data-tools/media/data-source-configuration-wizard.png) 在 Northwind 示例数据库中创建基于 `Customers` 和 `Orders` 表的数据源。  
  
#### 创建数据源  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
2.  在**“数据源”**窗口中，选择**“添加新数据源”**以启动**“数据源配置向导”**。  
  
3.  在**“选择数据源类型”**页上选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择你的数据连接”**页面上，执行以下操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         \- 或 \-  
  
    -   选择**“新建连接”**以启动**“添加\/修改连接”**对话框，并创建到 Northwind 数据库的连接。  
  
5.  如果数据库需要密码，请选择该选项以包括敏感数据，再单击**“下一步”**。  
  
6.  在**“将连接字符串保存到应用程序配置文件”**页面上单击**“下一步”**。  
  
7.  在**“选择数据库对象”**页面上展开**“表”**节点。  
  
8.  选择 `Customers` 和 `Orders` 表，然后单击**“完成”**。  
  
     **“NorthwindDataSet”**将会添加到你的项目中，并且**“数据源”**窗口中将显示 `Customers` 和 `Orders` 表。  
  
## 将控件添加到窗体  
 通过将某些项从**“数据源”**窗口拖到你的窗体上，可创建数据绑定控件。  
  
#### 在 Windows 窗体上创建数据绑定控件  
  
-   在**“数据源”**窗口中展开**“Customers”**节点。  
  
-   将主**“Customers”**节点从**“数据源”**窗口拖到**“Form1”**上。  
  
     用于导航记录的 <xref:System.Windows.Forms.DataGridView> 控件和工具栏（<xref:System.Windows.Forms.BindingNavigator>）将显示在窗体上。  组件栏中出现 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
-   将相关的**“Orders”**节点（**“Fax”**列下面的相关子表节点，而非主**“Orders”**节点）拖到**“CustomersDataGridView”**下面的窗体上。  
  
     窗体上显示一个 <xref:System.Windows.Forms.DataGridView>。  [OrdersTableAdapter](../data-tools/tableadapter-overview.md) 和 <xref:System.Windows.Forms.BindingSource> 将显示在组件栏中。  
  
## 添加对 System.Transactions 程序集的引用  
 事务使用 <xref:System.Transactions> 命名空间。  默认情况下，没有添加对 system.transactions 程序集的项目引用，因此你需要手动将其添加。  
  
#### 添加对 System.Transactions DLL 文件的引用  
  
1.  从**“项目”**菜单中，选择**“添加引用”**。  
  
2.  选择**“System.Transactions”**（在**“.NET”**选项卡上），然后单击**“确定”**。  
  
     对**“System.Transactions”**的引用将会添加到项目中。  
  
## 修改 BindingNavigator 的 SaveItem 按钮中的代码  
 默认情况下，由于第一个表已放在你的窗体上，因此代码将会添加到 <xref:System.Windows.Forms.BindingNavigator> 上保存按钮的 `click` 事件中。  你需要手动添加代码以更新所有附加的表。  对于此演练，我们将重构源自保存按钮的单击事件处理程序的现有保存代码，并创建更多的方法以根据是需要添加行还是需要删除行提供特定的更新功能。  
  
#### 修改自动生成的保存代码  
  
1.  双击**“CustomersBindingNavigator”**上的**“保存”**按钮（带有软盘图标的按钮）。  
  
2.  将 `CustomersBindingNavigatorSaveItem_Click` 方法替换为以下代码：  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 对相关数据的协调更改的顺序如下：  
  
-   删除子记录（在此情况下，从 `Orders` 表中删除记录）  
  
-   删除父记录（在此情况下，从 `Customers` 表中删除记录）  
  
-   插入父记录（在此情况下，在 `Customers` 表中插入记录）  
  
-   插入子记录（在此情况下，在 `Orders` 表中插入记录）  
  
#### 删除现有顺序  
  
-   将以下 `DeleteOrders` 方法添加到**“Form1”**：  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### 删除现有客户  
  
-   将以下 `DeleteCustomers` 方法添加到**“Form1”**：  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### 添加新客户  
  
-   将以下 `AddNewCustomers` 方法添加到**“Form1”**：  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### 添加新顺序  
  
-   将以下 `AddNewOrders` 方法添加到**“Form1”**：  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## 运行应用程序  
  
#### 运行应用程序  
  
-   按 F5 运行该应用程序。  
  
## 请参阅  
 [事务和并发](../Topic/Transactions%20and%20Concurrency.md)   
 [Oracle 分布式事务](../Topic/Oracle%20Distributed%20Transactions.md)   
 [如何：使用事务保存数据](../data-tools/save-data-by-using-a-transaction.md)   
 [System.Transactions 与 SQL Server 的集成](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)