---
title: "Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data services in Visual Studio"
  - "WCF Data Services, Visual Studio"
  - "ADO.NET Data Services, Visual Studio"
  - "WCF data services in Visual Studio"
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio
本演练演示如何创建一个承载于 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Web 应用程序中的简单 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，然后从 Windows 窗体应用程序中访问它。  
  
 在此演练中，将：  
  
-   创建 Web 应用程序以承载 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]。  
  
-   创建一个表示 Northwind 数据库中 Customers 表的 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]。  
  
-   创建 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]。  
  
-   创建一个客户端应用程序，并添加对 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]的引用。  
  
-   启用对该服务的数据绑定并生成用户界面。  
  
-   可以选择向应用程序添加筛选功能。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   Northwind 示例数据库。  
  
     如果没有在开发计算机中安装此数据库，可以从 [Microsoft 下载中心](http://go.microsoft.com/fwlink/?LinkID=98088)进行下载。  有关说明，请参阅[下载示例数据库](../Topic/Downloading%20Sample%20Databases.md)。  
  
## 创建服务  
 若要创建 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，你将添加一个 Web 项目，创建一个[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]，然后通过此模型创建服务。  
  
 首先，将添加一个 Web 项目以承载服务。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 创建 Web 项目  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**。  
  
2.  在**“新建项目”**对话框中，展开**“Visual Basic”**或**“Visual C\#”**和**“Web”**节点，然后选择**“ASP.NET Web 应用程序”**模板。  
  
3.  在**“名称”**文本框中，输入 NorthwindWeb，然后选择**“确定”**按钮。  
  
4.  在**“新建 ASP.NET 项目”**对话框的**“选择模板”**列表中，选择**“空”**，然后选择**“确定”**按钮。  
  
 在此步骤中，你将创建一个表示 Northwind 数据库中 Customers 表的 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]。  
  
#### 创建实体数据模型  
  
1.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
2.  在**“添加新项”**对话框中，选择**“数据”**节点，然后选择**“ADO.NET 实体数据模型”**项。  
  
3.  在**“名称”**文本框中，输入 `NorthwindModel`，然后选择**“添加”**按钮。  
  
     此时将显示实体数据模型向导。  
  
4.  在实体数据模型向导中，在**选择模型内容**页上，选择**数据库项的 EF 设计器**，然后再选择**下一步**按钮。  
  
5.  在**“选择你的数据连接”**页上执行下列步骤之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         \- 或 \-  
  
    -   选择**“新建连接”**按钮来配置新数据连接。  有关详细信息，请参阅[如何：创建到 SQL Server 数据库的连接](http://msdn.microsoft.com/zh-cn/360c340d-e5a6-4a7e-a569-e95d500be43d)。  
  
6.  如果数据库需要密码，请选择**“是，在连接字符串中包含敏感数据”**选项按钮，然后选择**“下一步”**按钮。  
  
    > [!NOTE]
    >  如果显示一个对话框，请选择**“是”**将该文件保存到你的项目中。  
  
7.  在**“选择你的版本”**页上，选择**“Entity Framework 5.0”**选项按钮，然后选择**“下一步”**按钮。  
  
    > [!NOTE]
    >  为了使用具有 WCF 服务的 Entity Framework 6 的最新版本，你需要安装 WCF Data Services Entity Framework Provider NuGet 程序包。  请参阅[使用 WCF Data Services 5.6.0 与 Entity Framework 6\+](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx)。  
  
8.  在**“选择数据库对象”**页上，展开**“表”**节点、选中**“客户”**复选框，然后选择**“完成”**按钮。  
  
     随即显示实体模型关系图，NorthwindModel.edmx 文件也将添加到项目中。  
  
 在此步骤中，你将创建并测试数据服务。  
  
#### 创建数据服务  
  
1.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
2.  在**“添加新项”**对话框中，选择**“Web”**节点，然后选择**“WCF 数据服务 5.6”**项。  
  
3.  在**“名称”**文本框中，输入 `NorthwindCustomers`，然后选择**“添加”**按钮。  
  
     NorthwindCustomers.svc 文件将显示在**代码编辑器**中。  
  
4.  在**“代码编辑器”**中，定位到第一个 `TODO:` 注释并使用以下内容替换该代码：  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-cs[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  使用下面的代码替换 `InitializeService` 事件处理程序中的注释：  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-cs[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  在菜单栏上，依次选择**“调试”**、**“开始执行\(不调试\)”**以运行服务。  此时将打开一个浏览窗口，并显示该服务的 XML 架构。  
  
7.  在**地址**栏中，在 NorthwindCustomers.svc 的 URL 末尾处输入 `Customers`，然后按 Enter 键。  
  
     Customers 表中的数据将以 XML 表示形式显示。  
  
    > [!NOTE]
    >  某些情况下，Internet Explorer 会将数据错误解释为 RSS 源。  必须确保禁用显示 RSS 源的选项。  有关详细信息，请参阅[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)。  
  
8.  关闭浏览器窗口。  
  
 在接下来的步骤中，将创建一个 Windows 窗体客户端应用程序以使用该服务。  
  
## 创建客户端应用程序  
 若要创建客户端应用程序，你将另外添加一个项目，添加对该项目的服务引用，配置数据源，并创建一个用户界面以显示服务中的数据。  
  
 在第一个步骤中，你将 Windows 窗体项目添加到解决方案中，并将其设置为启动项目。  
  
#### 创建客户端应用程序  
  
1.  在菜单栏上，依次选择“文件”、**“添加”**、**“新建项目”**。  
  
2.  在**“新建项目”**对话框中，展开**“Visual Basic”**或**“Visual C\#”**节点，选择**“Windows”**节点，然后选择**“Windows 窗体应用程序”**。  
  
3.  在**“名称”**文本框中，输入 `NorthwindClient`，然后选择**“确定”**按钮。  
  
4.  在**解决方案资源管理器**中，选择 **NorthwindClient** 项目节点。  
  
5.  在菜单栏上，选择**“项目”**、**“设为启动项目”**。  
  
 在此步骤中，将添加对 Web 项目中的 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]的服务引用。  
  
#### 添加服务引用  
  
1.  在菜单栏上，依次选择**“项目”**、**“添加服务引用”**。  
  
2.  在**“添加服务引用”**对话框中，选择**“发现”**按钮。  
  
     NorthwindCustomers 服务的 URL 将显示在**“地址”**字段中。  
  
3.  选择**“确定”**按钮以添加服务引用。  
  
 在此步骤中，将配置数据源以启用对服务的数据绑定。  
  
#### 启用对服务的数据绑定  
  
1.  在菜单栏上，依次选择**“视图”**、**“其他窗口”**、**“数据源”**。  
  
2.  在**“数据源”**窗口中，选择**“添加新数据源”**按钮。  
  
3.  在**数据源配置向导**的**“选择数据源类型”**页上，选择**“对象”**，然后选择**“下一步”**按钮。  
  
4.  在**“选择数据对象”**页上，展开**“NorthwindClient”**节点，然后展开**“NorthwindClient.ServiceReference1”**节点。  
  
5.  选中**“Customer”**复选框，然后选择**“完成”**按钮。  
  
 在此步骤中，你将创建用于显示服务中的数据的用户界面。  
  
#### 创建用户界面  
  
1.  在**“数据源”**窗口中，打开**“Customers”**节点的快捷菜单，然后选择**“复制”**。  
  
2.  在**“Form1.vb”**或**“Form1.cs”**窗体设计器中，打开快捷菜单并选择**“粘贴”**。  
  
     一个 <xref:System.Windows.Forms.DataGridView> 控件、一个 <xref:System.Windows.Forms.BindingSource> 组件以及一个 <xref:System.Windows.Forms.BindingNavigator> 组件将添加到窗体中。  
  
3.  选择 **CustomersDataGridView** 控件，然后在**属性**窗口设置**停靠**属性进行**填充**。  
  
4.  在**解决方案资源管理器**中，打开 **Form1** 节点的快捷菜单，然后选择**查看代码**以打开代码编辑器，并在文件顶部添加以下 Imports 或 Using 语句：  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```c#  
    using NorthwindClient.ServiceReference1;  
    ```  
  
5.  将以下代码添加到 `Form1_Load` 事件处理程序中：  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
            Dim proxy As New NorthwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
            Me.CustomersBindingSource.DataSource = proxy.Customers  
        End Sub  
    ```  
  
    ```c#  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  在**解决方案资源管理器**中，打开 NorthwindCustomers.svc 文件的快捷菜单，然后选择**“在浏览器中查看”**。  此时将打开 Internet Explorer，并显示该服务的 XML 架构。  
  
7.  从 Internet Explorer 地址栏中复制 URL。  
  
8.  在步骤 4 中添加的代码中，选择 `http://localhost:53161/NorthwindCustomers.svc/` 并使用刚刚复制的 URL 替换它。  
  
9. 在菜单栏上，依次选择**“调试”**和**“启动调试”**以运行应用程序。  此时将显示客户信息。  
  
 现在，你有了一个可以使用的应用程序，该应用程序将显示 NorthwindCustomers 服务中的客户的列表。  如果希望通过该服务公开其他数据，则可以修改[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]以包括 Northwind 数据库中的其他表。  
  
 在下一个可选步骤中，将学习如何筛选服务返回的数据。  
  
## 添加筛选功能  
 在此步骤中，将自定义应用程序以根据客户的城市筛选数据。  
  
#### 添加根据城市进行筛选的功能  
  
1.  在**解决方案资源管理器**中，打开**“Form1.vb”**或**“Form1.cs”**节点的快捷菜单，然后选择**“打开”**。  
  
2.  将<xref:System.Windows.Forms.TextBox>工具箱中的 <xref:System.Windows.Forms.Button> 控件和  **控件添加到窗体。**  
  
3.  打开 <xref:System.Windows.Forms.Button> 控件的快捷菜单，选择**“查看代码”**，然后在 `Button1_Click` 事件处理程序中添加以下代码：  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```c#  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  在以上代码中，使用 `http://localhost:53161/NorthwindCustomers.svc` 事件处理程序中的 URL 替换 `Form1_Load`。  
  
5.  在菜单栏上，依次选择**“调试”**和**“启动调试”**以运行应用程序。  
  
6.  在文本框中，输入 London，然后选择相应的按钮。  将仅显示来自 London 的客户。  
  
## 请参阅  
 [How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)