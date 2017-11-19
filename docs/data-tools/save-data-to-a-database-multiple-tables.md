---
title: "将数据保存到数据库 （多个表） |Microsoft 文档"
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: e6ed4bf0cb025feb2a4f52084857d9bdf5394770
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="save-data-to-a-database-multiple-tables"></a>将数据保存到数据库 （多个表）
应用程序开发中最常用方案之一是在 Windows 应用程序窗体上显示数据、编辑数据并将更新后的数据发回数据库。 本演练创建可显示两个相关表的数据的窗体，并显示如何编辑记录和将更改保存回数据库。 此示例使用源自 Northwind 示例数据库的 `Customers` 和 `Orders` 表。  
  
 通过调用 TableAdapter 的 `Update` 方法，可以将应用程序中的数据保存回数据库。 将表从**数据源**自动添加到窗体，将保存数据所需的代码的窗口。添加到窗体的任何其他表都要求手动添加此代码。 本演练显示了如何添加从多个表保存更新的代码。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与不同帮助中的描述具体取决于你现用的设置或要使用的版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
 本演练涉及以下任务：  
  
-   创建一个新**Windows 窗体应用程序**项目。  
  
-   创建和配置将应用程序中的数据源[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)。  
  
-   设置中的项的控件[数据源窗口](add-new-data-sources.md)。 有关详细信息，请参阅[设置从数据源窗口拖动时创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   通过将某些项从创建数据绑定控件**数据源**拖动到窗体的窗口。  
  
-   修改数据集中的每个表中的几个记录。  
  
-   修改用于将数据集中的更新后的数据发回数据库的代码。  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**数据存储和处理**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
## <a name="create-the-windows-forms-application"></a>创建 Windows 窗体应用程序  
 第一步是创建**Windows 窗体应用程序**。 在此步骤中，为项目分配名称是可选的但我们将为其命名，因为我们将更高版本保存项目。  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>若要创建新的 Windows 窗体应用程序项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**UpdateMultipleTablesWalkthrough**，然后选择**确定**。 
  
     **UpdateMultipleTablesWalkthrough**创建项目并将其添加到**解决方案资源管理器**。  
  
## <a name="create-the-data-source"></a>创建数据源  
 此步骤创建一个数据源从 Northwind 数据库使用**数据源配置向导**。 你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。 有关设置 Northwind 示例数据库的信息，请参阅[如何： 安装示例数据库](../data-tools/installing-database-systems-tools-and-samples.md)。  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  上**数据**菜单上，选择**显示数据源**。  
  
2.  在**数据源**窗口中，选择**添加新数据源**启动**数据源配置向导**。  
  
3.  上**选择数据源类型**屏幕上，选择**数据库**，然后选择**下一步**。  
  
4.  上**选择你的数据连接**屏幕执行下列操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         - 或 -  
  
    -   选择**新连接**以打开**添加/修改连接**对话框。  
  
5.  如果你的数据库需要密码，选择该选项以包括敏感数据，然后选择**下一步**。  
  
6.  上**将连接字符串保存到应用程序配置文件**，选择**下一步**。  
  
7.  上**选择数据库对象**屏幕中，展开**表**节点。  
  
8.  选择**客户**和**订单**表，，然后选择**完成**。  
  
     **NorthwindDataSet**添加到你的项目，并且表将显示在**数据源**窗口。  
  
## <a name="set-the-controls-to-be-created"></a>设置要创建的控件  
 对于本演练中的数据`Customers`表位于**详细信息**其中的数据显示在单独的控件的布局。 中的数据`Orders`表位于**网格**中显示的布局<xref:System.Windows.Forms.DataGridView>控件。  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>设置“数据源”窗口中项的拖放类型  
  
1.  在**数据源**窗口中，展开**客户**节点。  
  
2.  上**客户**节点中，选择**详细信息**从控件列表中，若要更改的控件**客户**为单个控件的表。 有关详细信息，请参阅[设置从数据源窗口拖动时创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
## <a name="create-the-data-bound-form"></a>创建数据绑定窗体  
 你可以通过将某些项从创建数据绑定控件**数据源**拖动到窗体的窗口。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>在窗体上创建数据绑定控件  
  
1.  将主**客户**节点从**数据源**窗口拖到**Form1**。  
  
     带有描述性标签的数据绑定控件将显示在窗体上，同时还显示一个工具条 (<xref:System.Windows.Forms.BindingNavigator>)，用于在记录间进行导航。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， `CustomersTableAdapter`， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。  
  
2.  将相关**订单**节点从**数据源**窗口拖到**Form1**。  
  
    > [!NOTE]
    >  相关**订单**节点位于下面**传真**列是的子节点和**客户**节点。  
  
     用于导航记录的 <xref:System.Windows.Forms.DataGridView> 控件和工具栏（<xref:System.Windows.Forms.BindingNavigator>）将显示在窗体上。 `OrdersTableAdapter`和<xref:System.Windows.Forms.BindingSource>组件栏中出现。  
  
## <a name="add-code-to-update-the-database"></a>添加代码以更新数据库  
 你可以通过调用来更新数据库`Update`方法**客户**和**订单**Tableadapter。 默认情况下，事件处理程序**保存**按钮<xref:System.Windows.Forms.BindingNavigator>将添加到窗体的代码将更新发送到数据库。 此过程将修改代码以按正确的顺序发送更新。这将消除产生引用完整性错误的可能性。 该代码还将通过在 try-catch 块中包装更新调用来实现错误处理。 可以根据应用程序的需要修改代码。  
  
> [!NOTE]
>  为了清楚起见，本演练未使用事务。但是，如果你在更新两个或多个相关表，包括在一个事务内的所有更新逻辑。 事务是它首先确保对数据库的所有相关的更改均成功，任何更改在提交之前的进程。 有关详细信息，请参阅[事务和并发性](/dotnet/framework/data/adonet/transactions-and-concurrency)。  
  
#### <a name="to-add-update-logic-to-the-application"></a>将更新逻辑添加到应用程序  
  
1.  选择**保存**按钮上<xref:System.Windows.Forms.BindingNavigator>。这将打开代码编辑器`bindingNavigatorSaveItem_Click`事件处理程序。  
  
2.  替换事件处理程序中的代码以调用相关 TableAdapter 的 `Update` 方法。 下面的代码首先创建三个临时数据表以保存每个 <xref:System.Data.DataRowState> 的更新信息（<xref:System.Data.DataRowState.Deleted>、<xref:System.Data.DataRowState.Added> 和 <xref:System.Data.DataRowState.Modified>）。 然后更新的正确的顺序运行。 代码应类似于：  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## <a name="test-the-application"></a>测试应用程序  
  
#### <a name="to-test-the-application"></a>测试应用程序  
  
1.  选择**F5**。  
  
2.  对每个表中的一条或多条记录的数据执行一些更改。  
  
3.  选择**保存**按钮。  
  
4.  检查数据库中的值以验证更改是否已保存。  
  
  
## <a name="see-also"></a>另请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)