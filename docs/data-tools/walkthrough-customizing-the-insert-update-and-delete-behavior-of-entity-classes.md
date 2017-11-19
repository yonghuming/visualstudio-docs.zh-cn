---
title: "演练： 自定义插入、 更新和删除的实体类的行为 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f711c0fcdd4866a1b097585052cdcb3733e426d8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>演练： 自定义插入、 更新和删除的实体类的行为
[LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供用于创建和编辑的可视化设计图面[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]基于数据库中的对象的类 （实体类）。 通过使用[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)，你可以使用 LINQ 技术访问 SQL 数据库。 有关详细信息，请参阅 [LINQ（语言集成查询）](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)。  
  
默认情况下，由 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 运行时提供用于执行更新的逻辑。 该运行时基于表的架构（列定义和主键信息）创建默认的 Insert、Update 和 Delete 语句。 当不希望使用默认行为时，可以配置更新行为并指定特定的存储过程，来执行处理数据库中数据所必需的插入、更新和删除。 在不生成默认行为时（例如，实体类映射到视图时），也可以这样做。 另外，在数据库要求通过存储过程访问表时，您可以重写默认的更新行为。 有关详细信息，请参阅[自定义操作通过使用存储过程](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures)。  
  
> [!NOTE]
>  本演练需要的可用性**InsertCustomer**， **UpdateCustomer**，和**DeleteCustomer**存储 Northwind 数据库的过程。  
  
本演练提供了一些步骤，您必须执行这些步骤来重写默认的 LINQ to SQL 运行时行为，以便使用存储过程将数据保存回数据库。  
  
在本演练中，你将学习如何执行以下任务：  
  
-   创建一个新的 Windows 窗体应用程序，并将一个 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 文件添加到该应用程序。  
  
-   创建一个映射到 Northwind Customers 表的实体类。  
  
-   创建一个引用 LINQ to SQL Customer 类的对象数据源。  
  
-   创建一个包含绑定到 Customer 类的 <xref:System.Windows.Forms.DataGridView> 的 Windows 窗体。  
  
-   实现该窗体的保存功能。  
  
-   通过将存储过程添加到 <xref:System.Data.Linq.DataContext>来创建 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 方法。  
  
-   配置 Customer 类以使用存储过程执行插入、更新和删除。  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**数据存储和处理**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>创建一个应用程序并添加 LINQ to SQL 类  
因为您将要使用 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 类并在 Windows 窗体中显示数据，所以需要创建一个新的 Windows 窗体应用程序并添加一个 LINQ to SQL 类文件。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>若要创建包含 LINQ to SQL 类的新 Windows 窗体应用程序项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**UpdatingWithSProcsWalkthrough**，然后选择**确定**。 
  
     **UpdatingWithSProcsWalkthrough**项目时创建，并添加到**解决方案资源管理器**。  
  
4.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
5.  单击**LINQ to SQL 类**模板和类型**Northwind.dbml**中**名称**框。  
  
6.  单击 **“添加”**。  
  
     这会将一个空的 LINQ to SQL 类文件 (Northwind.dbml) 添加到该项目中，并且会打开 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>创建 Customer 实体类和对象数据源  
 创建[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]通过拖动来自表映射到数据库表的类**服务器资源管理器**/**数据库资源管理器**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 结果将生成映射到数据库中的表的 LINQ to SQL 实体类。 在创建实体类后，可以将这些类像具有公共属性的其他类一样用作对象数据源。  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>创建 Customer 实体类并使用该类配置数据源  
  
1.  在**服务器资源管理器**/**数据库资源管理器**，查找 Northwind 示例数据库的 SQL Server 版本中的客户表。 
  
2.  拖动**客户**节点从**服务器资源管理器**/**数据库资源管理器**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]面。  
  
     名为的实体类**客户**创建。 该类具有与 Customers 表中的列相对应的属性。 实体类命名为**客户**(不**客户**) 因为它代表单个客户 Customers 表中。  
  
    > [!NOTE]
    >  此重命名行为称为*复数形式*。 它可以打开或关闭[选项对话框](../ide/reference/options-dialog-box-visual-studio.md)。 有关详细信息，请参阅[如何： 打开和关闭 （O/R 设计器） 的复数形式](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)。  
  
3.  上**生成**菜单上，单击**生成 UpdatingwithSProcsWalkthrough**以生成项目。  
  
4.  在 **“数据”** 菜单上，单击 **“显示数据源”**。  
  
5.  在 **“数据源”** 窗口中，单击 **“添加新数据源”**。  
  
6.  单击**对象**上**选择数据源类型**页，然后单击**下一步**。  
  
7.  展开**UpdatingwithSProcsWalkthrough**节点然后找到并选择**客户**类。  
  
    > [!NOTE]
    >  如果**客户**类不可用、 退出向导、 生成项目时，和重新运行该向导。  
8.  单击**完成**以创建数据源并添加**客户**到实体类**数据源**窗口。  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>创建一个 DataGridView 以在 Windows 窗体中显示 Customer 数据  
 创建绑定到实体类通过拖动的控件[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]数据源项从**数据源**拖到 Windows 窗体的窗口。  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>添加绑定到实体类的控件  
  
1.  在“设计”视图中打开“Form1”。  
  
2.  从**数据源**窗口中，拖动**客户**节点拖到 Form1 上的。  
  
    > [!NOTE]
    >  若要显示**数据源**窗口中，单击**显示数据源**上**数据**菜单。  
  
3.  在代码编辑器中打开 Form1。  
  
4.  将下面的代码添加到该窗体中。这些代码对于该窗体是全局性的，位于任何特定方法之外，但位于 Form1 类内部：  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();    
    ```  
  
5.  为 `Form_Load` 事件创建一个事件处理程序，并将下面的代码添加到该处理程序中：  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;    
    ```  
  
## <a name="implementing-save-functionality"></a>实现保存功能  
 默认情况下，没有启用保存按钮，也没有实现保存功能。 此外，在为对象数据源创建数据绑定控件时，不会自动添加用于将更改后的数据保存到数据库的代码。 本节说明如何为 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 对象启用保存按钮并实现保存功能。  
  
#### <a name="to-implement-save-functionality"></a>实现保存功能  
  
1.  在“设计”视图中打开“Form1”。  
  
2.  选择保存按钮上**CustomerBindingNavigator** （带有软盘图标的按钮）。  
  
3.  在**属性**窗口中，设置**已启用**属性**True**。  
  
4.  双击保存按钮以创建一个事件处理程序并切换到代码编辑器。  
  
5.  将下面的代码添加到保存按钮事件处理程序中：  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>重写用于执行更新（插入、更新和删除）的默认行为  
  
#### <a name="to-override-the-default-update-behavior"></a>重写默认更新行为  
  
1.  在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中打开“LINQ to SQL”文件。 (双击**Northwind.dbml**文件中**解决方案资源管理器**。)  
  
2.  在**服务器资源管理器**/**数据库资源管理器**，展开 Northwind 数据库**存储过程**节点并找到**InsertCustomers**， **UpdateCustomers**，和**DeleteCustomers**存储过程。  
  
3.  将所有这三个存储过程都拖动到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上。  
  
     这些存储过程将作为 <xref:System.Data.Linq.DataContext> 方法添加到方法窗格中。 有关详细信息，请参阅[DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
4.  选择**客户**中的实体类[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
5.  在**属性**窗口中，选择**插入**属性。  
  
6.  单击旁边的省略号 （...）**使用运行时**以打开**配置行为**对话框。  
  
7.  选择**自定义**。  
  
8.  选择**InsertCustomers**中的方法**自定义**列表。  
  
9. 单击**应用**以保存所选择的类和行为配置。  
  
    > [!NOTE]
    >  你可以继续配置为每个类/行为组合的行为，只要你单击**应用**每次更改后。 如果你更改类或行为之前单击**应用**、 提供机会应用任何更改将出现一个警告对话框。  
  
10. 选择**更新**中**行为**列表。  
  
11. 选择**自定义**。  
  
12. 选择**UpdateCustomers**中的方法**自定义**列表。  
  
     检查的列表**方法自变量**和**类属性**，并注意有两个**方法自变量**和两个**类属性**对于表中的某些列。 这样可以更加轻松地跟踪更改和创建检查并发冲突的语句。  
  
13. 映射**Original_CustomerID**方法自变量**CustomerID （原始）**类属性。  
  
    > [!NOTE]
    >  默认情况下，当名称匹配时，方法自变量会映射到类属性。 如果属性名称发生更改并且在表与实体类之间不再匹配，则在 O/R 设计器无法确定正确的映射时，您可能必须选择等效的类属性进行映射。 此外，如果方法自变量没有用于进行映射到的有效类属性，则可以设置**类属性**值赋给**（无）**。  
  
14. 单击**应用**以保存所选择的类和行为配置。  
  
15. 选择**删除**中**行为**列表。  
  
16. 选择**自定义**。  
  
17. 选择**DeleteCustomers**中的方法**自定义**列表。  
  
18. 映射**Original_CustomerID**方法自变量**CustomerID （原始）**类属性。  
  
19. 单击“确定”。  
  
> [!NOTE]
>  在本演练中，虽然以下事实并不会产生问题，但仍然需要注意：[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 会在插入和更新操作期间自动为标识（自动递增）列、rowguidcol（数据库生成的 GUID）列以及时间戳列处理数据库生成的值。 在其他列类型中，数据库生成的值将意外导致 Null 值。 若要返回数据库生成的值，应手动将 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 设置为 `true` 并将 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 设置为下列值之一：<xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync> 或 <xref:System.Data.Linq.Mapping.AutoSync>。  
  
## <a name="testing-the-application"></a>测试应用程序  
 运行应用程序再次确认**UpdateCustomers**存储的过程是否能够正确更新数据库中的客户记录。  
  
#### <a name="to-test-the-application"></a>测试应用程序  
  
1.  按 F5。  
  
2.  修改网格中的一条记录以测试更新行为。  
  
3.  添加一条新记录以测试插入行为。  
  
4.  单击“保存”按钮将更改保存回数据库。  
  
5.  关闭窗体。  
  
6.  按 F5 并验证是否保存了更新的记录和新插入的记录。  
  
7.  删除在步骤 3 中创建的新记录以测试删除行为。  
  
8.  单击保存按钮以提交更改并从数据库中移除已删除的记录  
  
9. 关闭窗体。  
  
10. 按 F5 并验证是否从数据库中移除了已删除的记录。  
  
    > [!NOTE]
    >  如果你的应用程序将使用 SQL Server Express Edition，具体取决于值**复制到输出目录**数据库文件的属性，所做的更改时可能会不显示在步骤 10 中按 F5。 
  
## <a name="next-steps"></a>后续步骤  
根据应用程序要求的不同，您可能需要在创建 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 实体类后执行几个步骤。 你可以对此应用程序进行的一些增强包括：  
  
-   在更新过程中实现并发检查。 有关信息，请参阅[开放式并发： 概述](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview)。  
  
-   添加 LINQ 查询以筛选数据。 有关信息，请参阅[LINQ 查询 (C#) 简介](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
## <a name="see-also"></a>请参阅
[LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)     
[DataContext 方法](../data-tools/datacontext-methods-o-r-designer.md)   
[如何： 分配存储的过程以便执行更新、 插入和删除](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)  
[LINQ to SQL 查询](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)  
 