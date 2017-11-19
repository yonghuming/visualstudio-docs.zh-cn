---
title: "演练： 创建 N 层数据应用程序 |Microsoft 文档"
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
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 22ea6a58453de8c28703dbe0252ab6370be55bf3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>演练：创建 N 层数据应用程序
*N 层*数据应用程序是应用程序访问数据且分为多个逻辑层，或*层*。 通过将应用程序组件分离到相对独立的层中，可以提高应用程序的可维护性和可伸缩性。 该结构之所以具有这种优点，是因为它有利于采用可应用于单个层而无需重新设计整个解决方案的新技术。 N 层体系结构包括一个表示层、一个中间层和一个数据层。 中间层通常包括数据访问层、业务逻辑层和共享组件（例如身份验证和验证）。 数据层则包括关系数据库。 N 层应用程序通常将敏感信息存储在中间层的数据访问层中，目的是将它们与访问表示层的最终用户隔离。 有关详细信息，请参阅[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)。  
  
在 N 层应用程序中，分离各层的一种方法是为要包括在应用程序中的每一层创建相互独立的项目。 类型化数据集包含一个 `DataSet Project` 属性，该属性决定了生成的数据集和 `TableAdapter` 代码应归属到哪些项目中。  
  
本演练演示如何隔离数据集和`TableAdapter`代码分离到相互独立库项目通过使用**数据集设计器**。 分隔的数据集和 TableAdapter 代码后，你将创建[Windows Communication Foundation 服务和 Visual Studio 中的 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)服务以调入数据访问层。 最后，你要创建一个 Windows 窗体应用程序并将其用作表示层。 该层将访问数据服务中的数据。  
  
在本演练中，你将执行以下步骤：  
  
-   新建将包含多个项目的 N 层解决方案。  
  
-   将两个类库项目添加到 N 层解决方案中。  
  
-   通过创建类型化数据集**数据源配置向导**。  
  
-   将生成[Tableadapter](create-and-configure-tableadapters.md)和数据集代码分离到离散的项目。  
  
-   创建 Windows Communication Foundation (WCF) 服务以调入数据访问层。  
  
-   在服务中创建函数以从数据访问层检索数据。  
  
-   创建 Windows 窗体应用程序来充当表示层。  
  
-   创建绑定到数据源的 Windows 窗体控件。  
  
-   编写代码以填充数据表。  
  
![视频链接](../data-tools/media/playvideo.gif "PlayVideo")本主题的视频版本，请参阅[视频帮助： 创建 N 层数据应用程序](http://go.microsoft.com/fwlink/?LinkId=115188)。  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**.NET 桌面开发**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>创建 N 层解决方案和用于保存数据集的类库 (DataEntityTier)  
 本演练的第一步是创建一个解决方案和两个类库项目。 第一个类库将保存数据集（生成的类型化 DataSet 类以及将保存应用程序数据的数据表）。 此项目将用作应用程序的数据实体层，它通常位于中间层内。 用于创建初始数据集和自动将代码分离到两个类库 datasetis。  
  
> [!NOTE]
>  请务必正确命名项目和解决方案，然后再单击**确定**。 这样做可使你更轻松地完成本演练。  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>创建 N 层解决方案和 DataEntityTier 类库  

1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**类库**项目类型。  
  
4. 将项目**DataEntityTier**。  
  
5. 将解决方案命名**NTierWalkthrough**，然后选择**确定**。  
  
     创建包含 DataEntityTier 项目的 NTierWalkthrough 解决方案并将其添加到**解决方案资源管理器**。  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>创建用于保存 TableAdapter 的类库 (DataAccessTier)  
 创建 DataEntityTier 项目后，下一步是创建另一个类库项目。 此项目将保存生成`TableAdapter`s 和称为*数据访问层*的应用程序。 数据访问层包含连接到数据库所需的信息，通常位于中间层内。  
  
#### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>若要为 Tableadapter 创建单独的类库  
  
1.  右键单击解决方案资源管理器中的解决方案，然后选择**添加**，**新项目...**.  
  
2.  在**新项目**对话框中，在中间的窗格中，选择**类库**。  
  
3.  将项目**DataAccessTier**选择**确定**。  
  
     DataAccessTier 项目即被创建并添加到 NTierWalkthrough 解决方案中。  
  
## <a name="creating-the-dataset"></a>创建数据集  
 下一步是创建类型化数据集。 通过单个项目中的数据集类（包括 DataTable 类）和 `TableAdapter` 类创建类型化数据集。 （所有类都将生成到单个文件中。）在将数据集和 `TableAdapter` 分离到不同的项目中时，移到另一个项目中的是数据集类，`TableAdapter` 类则留在原始项目中。 因此，应在最终包含 `TableAdapter` 的项目（DataAccessTier 项目）中创建数据集。 你将通过创建数据集**数据源配置向导**。  
  
> [!NOTE]
>  你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。 有关如何设置 Northwind 示例数据库的信息，请参阅[如何： 安装示例数据库](../data-tools/installing-database-systems-tools-and-samples.md)。  
  
#### <a name="to-create-the-dataset"></a>创建数据集  
  
1.  选择在 DataAccessTier**解决方案资源管理器**。  
  
2.  上**数据**菜单上，选择**显示数据源**。  
  
3.  在**数据源**窗口中，选择**添加新数据源**启动**数据源配置向导**。  
  
4.  上**选择数据源类型**页上，选择**数据库**，然后选择**下一步**。  
  
5.  上**选择你的数据连接**页上，执行以下操作之一：  
  
     如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
     - 或 -  
  
     选择**新连接**以打开**添加连接**对话框。  
  
6.  如果数据库需要密码，请选择该选项以包括敏感数据，然后选择**下一步**。  
  
    > [!NOTE]
    >  如果选择了本地数据库文件（而不是连接至 SQL Server），系统可能会询问你是否将该文件添加到项目中。 选择**是**将数据库文件添加到项目。  
  
7.  选择**下一步**上**将连接字符串保存到应用程序配置文件**页。  
  
8.  在 **“选择数据库对象”** 页面上展开 **“表”** 节点。  
  
9.  选择对应的复选框**客户**和**订单**表，，然后选择**完成**。  
  
     NorthwindDataSet 将添加到 DataAccessTier 项目，并出现在**数据源**窗口。  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>将 TableAdapter 与数据集分离  
 创建数据集后，接着是要将生成的数据集类与 TableAdapter 分离。 执行此操作通过设置**数据集项目**属性设置为在其中存储分离出的数据集类项目的名称。  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>将 TableAdapter 与数据集分离  
  
1.  双击**NorthwindDataSet.xsd**中**解决方案资源管理器**以打开中的数据集**数据集设计器**。  
  
2.  选择设计器上的空白区域。  
  
3.  找到**数据集项目**中的节点**属性**窗口。  
  
4.  在**数据集项目**列表中，选择**DataEntityTier**。  
  
5.  上**生成**菜单上，选择**生成解决方案**。  
  
 将数据集和 TableAdapter 分离到两个类库项目中。 最初包含整个数据集的项目 (DataAccessTier) 现在只包含 TableAdapter。 中指定的项目**数据集项目**属性 (DataEntityTier) 包含类型化数据集： NorthwindDataSet.Dataset.Designer.vb （或 NorthwindDataSet.Dataset.Designer.cs）。  
  
> [!NOTE]
>  当你将数据集和 Tableadapter (通过设置**数据集项目**属性)，将不会自动移动项目中的现有数据集分部类。 你必须手动将它们移到数据集项目中。  
  
## <a name="creating-a-new-service-application"></a>创建新的服务应用程序  
本演练演示如何通过 WCF 服务访问数据访问层，因此让我们来创建新的 WCF 服务应用程序。  
  
#### <a name="to-create-a-new-wcf-service-application"></a>创建新的 WCF 服务应用程序  
  
1.  右键单击解决方案资源管理器中的解决方案，然后选择**添加**，**新项目...**.  
  
2.  在**新项目**对话框中，在左侧的窗格中，选择**WCF**。  在中间窗格中，选择**WCF 服务库**。  
  
3.  将项目**DataService**和选择**确定**。  
  
     DataService 项目即被创建并添加到 NTierWalkthrough 解决方案中。  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>在数据访问层中创建用于返回客户和订单数据的方法  
 数据服务需要调用数据访问层中的两个方法：GetCustomers 和 GetOrders。 这些方法将返回 Northwind 的 Customers 表和 Orders 表。 请在 DataAccessTier 项目中创建 GetCustomers 和 GetOrders 方法。  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>在数据访问层中创建返回 Customers 表的方法  
  
1.  在**解决方案资源管理器**，双击 NorthwindDataset.xsd 打开数据集。
  
2.  右键单击 CustomersTableAdapter 然后单击**添加查询**。  
  
3.  上**选择命令类型**页上，保留默认值为**使用 SQL 语句**单击**下一步**。  
  
4.  上**选择查询类型**页上，保留默认值为**返回行的选择**单击**下一步**。  
  
5.  上**指定 SQL SELECT 语句**页上，保留默认查询，单击**下一步**。  
  
6.  上**选择要生成的方法**页上，键入**GetCustomers**为**方法名称**中**返回 DataTable**部分。  
  
7.  单击 **“完成”**。  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>在数据访问层中创建返回 Orders 表的方法  
  
1.  右键单击 OrdersTableAdapter，然后单击**添加查询**。  
  
2.  上**选择命令类型**页上，保留默认值为**使用 SQL 语句**单击**下一步**。  
  
3.  上**选择查询类型**页上，保留默认值为**返回行的选择**单击**下一步**。  
  
4.  上**指定 SQL SELECT 语句**页上，保留默认查询，单击**下一步**。  
  
5.  上**选择要生成的方法**页上，键入**GetOrders**为**方法名称**中**返回 DataTable**部分。  
  
6.  单击 **“完成”**。  
  
7.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>向数据服务中添加对数据实体和数据访问层的引用  
 由于数据服务需要数据集和 TableAdapter 中的信息，因此需要添加对 DataEntityTier 和 DataAccessTier 项目的引用。  
  
#### <a name="to-add-references-to-the-data-service"></a>添加对数据服务的引用  
  
1.  右键单击 DataService 中的**解决方案资源管理器**单击**添加引用**。  
  
2.  单击**项目**选项卡中**添加引用**对话框。  
  
3.  选择这两个**DataAccessTier**和**DataEntityTier**项目。  
  
4.  单击“确定”。  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>向服务中添加函数以调用数据访问层中的 GetCustomers 和 GetOrders 方法  
 现在数据访问层包含返回数据的方法，接下来要在数据服务中创建调用这些方法的方法。  
  
> [!NOTE]
>  对于 C# 项目，必须添加对 `System.Data.DataSetExtensions` 程序集的引用，才能编译下面的代码。  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>在数据服务中创建 GetCustomers 和 GetOrders 函数  
  
1.  在**DataService**项目中，双击 IService1.vb 或 IService1.cs。  
  
2.  添加以下代码在**添加您的服务操作**注释：  
  
    ```vb  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```csharp  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
    ```  
  
3.  在 DataService 项目中，双击 Service1.vb（或 Service1.cs）。  
  
4.  将以下代码添加到 Service1 类中：  
  
    ```vb  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```csharp  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
    }  
    ```  
  
5.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>创建表示层以显示数据服务中的数据  
 现在，解决方案中的数据服务已具有调入数据访问层的方法，接下来要创建另一个项目，以调入数据服务并将数据显示给用户。 对于本演练，创建一个 Windows 窗体应用程序；它将充当 N 层应用程序的表示层。  
  
#### <a name="to-create-the-presentation-tier-project"></a>创建表示层项目  
  
1.  右键单击解决方案资源管理器中的解决方案，然后选择**添加**，**新项目...**.  
  
2.  在**新项目**对话框中，在左侧的窗格中，选择**Windows 经典桌面**。 在中间窗格中，选择**Windows 窗体应用程序**。  
  
3.  将项目**PresentationTier**单击**确定**。  
  
    PresentationTier 项目即被创建并添加到 NTierWalkthrough 解决方案中。  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>将 PresentationTier 项目设置为启动项目  
我们将设置 PresentationTier 项目为启动项目解决方案，因为它是用于表示文本和与数据交互的实际客户端应用程序。  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>将新的表示层项目设置为启动项目  
  
-   在**解决方案资源管理器**，右键单击**PresentationTier**单击**设为启动项目**。  
  
## <a name="adding-references-to-the-presentation-tier"></a>添加对表示层的引用  
 客户端应用程序 PresentationTier 需要具有对数据服务的服务引用，才能访问服务中的方法。 另外，WCF 服务又需要具有对数据集的引用，才能启用类型共享。 而只有通过数据服务启用类型共享，表示层才能使用添加到数据集分部类中的代码。 由于数据表的行和列更改事件中通常添加有类似于验证的代码，因此可能需要从客户端访问此代码。  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>添加定义表示层的引用  
  
1.  在**解决方案资源管理器**，右键单击 PresentationTier，然后选择**添加引用**。  
  
2.  在**添加引用**对话框中，选择**项目**选项卡。  
  
3.  选择**DataEntityTier**选择**确定**。  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>添加对表示层的服务引用  
  
1.  在**解决方案资源管理器**，右键单击 PresentationTier，然后选择**添加服务引用**。  
  
2.  在**添加服务引用**对话框中，选择**发现**。  
  
3.  选择**Service1**选择**确定**。  
  
    > [!NOTE]
    >  如果当前计算机上存在多项服务，请选择你在本演练的前面部分中创建的服务（即包含 GetCustomers 和 GetOrders 方法的服务）。  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>将 DataGridView 添加到窗体，以显示数据服务返回的数据  
 添加对数据服务的服务引用后**数据源**服务返回的数据自动填充窗口。  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>将两个数据绑定 DataGridView 添加到窗体中  
  
1.  在**解决方案资源管理器**，选择 PresentationTier 项目。  
  
2.  在**数据源**窗口中，展开**NorthwindDataSet**并找到**客户**节点。  
  
3.  拖动**客户**节点拖到 Form1 上的。  
  
4.  在**数据源**窗口中，展开**客户**节点和查找相关**订单**节点 (**订单**节点嵌套在**客户**节点)。  
  
5.  将相关**订单**节点拖到 Form1 上的。  
  
6.  通过双击窗体的空白区域，创建一个 `Form1_Load` 事件处理程序。  
  
7.  将以下代码添加到 `Form1_Load` 事件处理程序中。  
  
    ```vb  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```csharp  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
    ```  
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>增加服务所允许的最大消息大小  
MaxReceivedMessageSize 的默认值不足够大以保存从 Customers 和 Orders 表检索的数据。 在以下步骤中，你将增加为 6553600 值。 你将更改上的客户端，会自动更新服务引用的值。  
  
> [!NOTE]
>  较小的默认大小旨在降低遭受拒绝服务 (DoS) 攻击的可能性。 有关详细信息，请参阅<xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>。  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>增加 maxReceivedMessageSize 值  
  
1.  在**解决方案资源管理器**，双击 PresentationTier 项目中的 app.config 文件。  
  
2.  找到**maxReceivedMessage**大小特性，然后将值更改`6553600`。  
  
## <a name="testing-the-application"></a>测试应用程序  
通过按运行该应用程序**F5**。 应用程序会从数据服务中检索 Customers 和 Orders 表的数据，并将检索到的数据显示在窗体上。  
  
## <a name="next-steps"></a>后续步骤  
 根据应用程序的需求，在基于 Windows 的应用程序中保存相关数据后，可能还要执行一些步骤。 例如，你可以对此应用程序进行以下增强：  
  
-   将验证添加到数据集。 
  
-   将其他方法添加到服务，以将数据更新回数据库。  
  
## <a name="see-also"></a>另请参阅  
 [处理在 n 层应用程序中的数据集](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [分层更新](../data-tools/hierarchical-update.md)   
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)