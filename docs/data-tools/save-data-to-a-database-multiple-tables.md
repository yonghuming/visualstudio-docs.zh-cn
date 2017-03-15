---
title: "演练：将数据保存到数据库（多个表） | Microsoft Docs"
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
  - "数据 [Visual Studio], 更新"
  - "保存数据, 演练"
  - "更新数据集, 演练"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：将数据保存到数据库（多个表）
应用程序开发中最常用方案之一是在 Windows 应用程序窗体上显示数据、编辑数据并将更新后的数据发回数据库。  本演练创建可显示两个相关表的数据的窗体，并显示如何编辑记录和将更改保存回数据库。  此示例使用源自 Northwind 示例数据库的 `Customers` 和 `Orders` 表。  
  
 通过调用 TableAdapter 的 `Update` 方法，可以将应用程序中的数据保存回数据库。  当从**“数据源”**窗口拖动项时，为拖放到窗体上的第一个表自动添加保存数据的代码。  添加到窗体的任何其他表都要求手动添加保存数据所需的所有代码。  本演练显示了如何添加从多个表保存更新的代码。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 本演练涉及以下任务：  
  
-   创建新的**“Windows 应用程序”**项目。  
  
-   使用[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)在应用程序中创建和配置数据源。  
  
-   在[“数据源”窗口](../Topic/Data%20Sources%20Window.md)中设置项的控件。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   通过将某些项从**“数据源”**窗口拖到你的窗体上来创建数据绑定控件。  
  
-   修改数据集的每个表中的若干条记录。  
  
-   修改用于将数据集中的更新后的数据发回数据库的代码。  
  
## 系统必备  
 若要完成本演练，你将需要：  
  
-   能够访问 Northwind 示例数据库。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建 Windows 应用程序  
 第一步是创建**“Windows 应用程序”**。  在此步骤中为项目指定名称是可选的，但由于我们打算稍后保存该项目，因此为它指定了一个名称。  
  
#### 创建新的 Windows 应用程序项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  将项目命名为 `UpdateMultipleTablesWalkthrough`。  
  
3.  选择**“Windows 应用程序”**，然后单击**“确定”**。  有关详细信息，请参阅[客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     **“UpdateMultipleTablesWalkthrough”**项目即被创建并添加到**“解决方案资源管理器”**中。  
  
## 创建数据源  
 此步骤使用**“数据源配置向导”**从 Northwind 数据库创建一个数据源。  你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。  有关设置 Northwind 示例数据库的信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
#### 创建数据源  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
2.  在**“数据源”**窗口中，单击**“添加新数据源”**以启动**“数据源配置向导”**。  
  
3.  在**“选择数据源类型”**页上选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择你的数据连接”**页面上，执行以下操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         \- 或 \-  
  
    -   选择**“新建连接”**以打开**“添加\/修改连接”**对话框。  
  
5.  如果数据库需要密码，请选择该选项以包括敏感数据，再单击**“下一步”**。  
  
6.  在**“将连接字符串保存到应用程序配置文件”**页面上单击**“下一步”**。  
  
7.  在**“选择数据库对象”**页面上展开**“表”**节点。  
  
8.  选择**“Customers”**和**“Orders”**表，然后单击**“完成”**。  
  
     **“NorthwindDataSet”**将添加到你的项目，这些表将显示在**“数据源”**窗口中。  
  
## 设置要创建的控件  
 对于本演练，`Customers` 表中的数据将位于**“详细信息”**布局（数据在单独控件中显示）中。  来自 `Orders` 表的数据将位于**“网格”**布局（在 <xref:System.Windows.Forms.DataGridView> 控件中显示）中。  
  
#### 设置“数据源”窗口中项的拖放类型  
  
1.  在**“数据源”**窗口中展开**“Customers”**节点。  
  
2.  通过从**“Customers”**节点上的控件列表中选择**“详细信息”**，将**“Customers”**表中的控件更改为单个控件。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
## 创建数据绑定窗体  
 通过将某些项从**“数据源”**窗口拖到你的窗体上，可创建数据绑定控件。  
  
#### 在窗体上创建数据绑定控件  
  
1.  将主**“Customers”**节点从**“数据源”**窗口拖到**“Form1”**上。  
  
     带有描述性标签的数据绑定控件将显示在窗体上，同时还显示一个工具条 \(<xref:System.Windows.Forms.BindingNavigator>\)，用于在记录间进行导航。  组件栏中出现 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
2.  将相关的**“Orders”**节点从**“数据源”**窗口拖到**“Form1”**上。  
  
    > [!NOTE]
    >  相关的**“Orders”**节点位于**“Fax”**列下，该节点是**“Customers”**节点的子节点。  
  
     用于导航记录的 <xref:System.Windows.Forms.DataGridView> 控件和工具栏（<xref:System.Windows.Forms.BindingNavigator>）将显示在窗体上。  [OrdersTableAdapter](../data-tools/tableadapter-overview.md) 和 <xref:System.Windows.Forms.BindingSource> 将显示在组件栏中。  
  
## 添加用于更新数据库的代码  
 通过调用**“Customers”**和**“Orders”**TableAdapter 的 `Update` 方法，可更新数据库。  默认情况下，<xref:System.Windows.Forms.BindingNavigator> 的**“保存”**按钮的事件处理程序将添加到窗体代码中，以将更新内容发送到数据库。  本过程将修改该代码以按正确的顺序发送更新内容，从而消除产生引用完整性错误的可能性。  该代码还将通过在 try\-catch 块中包装更新调用来实现错误处理。  可以根据应用程序的需要修改代码。  
  
> [!NOTE]
>  为了清楚起见，本演练未使用事务，但是如果你要更新两个或多个相关表，则应在一个事务中包含所有更新逻辑。  事务是指一个过程，它首先确保对数据库的所有相关更改均可成功完成，然后再提交更改。  有关详细信息，请参阅[事务和并发](../Topic/Transactions%20and%20Concurrency.md)。  
  
#### 将更新逻辑添加到应用程序  
  
1.  在 <xref:System.Windows.Forms.BindingNavigator> 上双击**“保存”**按钮，以打开代码编辑器并转到 `bindingNavigatorSaveItem_Click` 事件处理程序。  
  
2.  替换事件处理程序中的代码以调用相关 TableAdapter 的 `Update` 方法。  下面的代码首先创建三个临时数据表以保存每个 <xref:System.Data.DataRowState> 的更新信息（<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 和 <xref:System.Data.DataRowState>）。  然后，按正确的顺序执行更新。  代码应类似于：  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## 测试应用程序  
  
#### 测试应用程序  
  
1.  按 F5。  
  
2.  对每个表中的一条或多条记录的数据执行一些更改。  
  
3.  按**“保存”**按钮。  
  
4.  检查数据库中的值以验证更改是否已保存。  
  
## 后续步骤  
 根据应用程序的要求，在 Windows 应用程序中创建了绑定数据窗体后，还需要执行一些步骤。  你可以通过以下操作来增强此演练的效果：  
  
-   将搜索功能添加到该窗体。  有关详细信息，请参阅[如何：向 Windows 窗体应用程序中添加参数化查询](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)。  
  
-   编辑数据源以添加或移除数据库对象。  有关详细信息，请参阅[如何：编辑数据集](../Topic/How%20to:%20Edit%20a%20Dataset.md)。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)