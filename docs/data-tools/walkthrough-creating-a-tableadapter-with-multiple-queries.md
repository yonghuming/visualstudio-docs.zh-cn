---
title: "演练：创建带有多个查询的 TableAdapter | Microsoft Docs"
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
  - "数据 [Visual Studio], TableAdapter"
  - "数据 [Visual Studio], 演练"
  - "查询 [Visual Studio], TableAdapter"
  - "TableAdapter 查询, 创建"
  - "TableAdapter, 创建"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 演练：创建带有多个查询的 TableAdapter
在本演练中，将使用[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)在数据集中创建一个 TableAdapter。  本演练将指导你完成通过在[“数据集设计器”](../data-tools/creating-and-editing-typed-datasets.md)中使用 [TableAdapter 查询配置向导](../data-tools/editing-tableadapters.md)，从而在 [TableAdapter](../data-tools/tableadapter-overview.md) 中创建第二个查询的过程。  
  
 本演练涉及以下任务：  
  
-   创建新的**“Windows 应用程序”**项目。  
  
-   通过使用**“数据源配置向导”**生成数据集，在应用程序中创建和配置数据源。  
  
-   在**“数据集设计器”**中打开该新数据集。  
  
-   通过**“TableAdapter 配置向导”**将查询添加到 TableAdapter。  
  
## 系统必备  
 若要完成本演练，你需要：  
  
-   访问 Northwind 示例数据库（SQL Server 或 Access 版）。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建新的 Windows 应用程序  
 第一步是创建 Windows 应用程序。  
  
#### 创建新的 Windows 应用程序项目  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，从**“文件”**菜单创建一个新项目。  
  
2.  在**“项目类型”**窗格中选择一种编程语言。  
  
3.  在**“模板”**窗格中单击**“Windows 应用程序”**。  
  
4.  将项目命名为 `TableAdapterQueriesWalkthrough`，然后单击**“确定”**。  
  
     Visual Studio 随即将该项目添加到**“解决方案资源管理器”**，并在设计器中显示一个新窗体。  
  
## 使用 TableAdapter 创建数据库数据源  
 此步骤基于 Northwind 示例数据库中 `Customers` 表使用**“数据源配置向导”**创建数据源。  你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。  有关设置 Northwind 示例数据库的信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
#### 创建数据源  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
2.  在**“数据源”**窗口中，选择**“添加新数据源”**以启动**“数据源配置向导”**。  
  
3.  在**“选择数据源类型”**页上选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择你的数据连接”**页面上，执行以下操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         \- 或 \-  
  
    -   选择**“新建连接”**，以启动**“添加\/修改连接”**对话框。  
  
5.  如果数据库需要密码，请选择该选项以包括敏感数据，再单击**“下一步”**。  
  
6.  在**“将连接字符串保存到应用程序配置文件”**页面上单击**“下一步”**。  
  
7.  在**“选择数据库对象”**页面上展开**“表”**节点。  
  
8.  选择**“Customers”**表，然后单击**“完成”**。  
  
     **“NorthwindDataSet”**即被添加到你的项目中，并且**“数据源”**窗口中将显示**“Customers”**表。  
  
## 在数据集设计器中打开数据集  
  
#### 在“数据集设计器”中打开数据集  
  
1.  在**“数据源”**窗口中右键单击**“NorthwindDataset”**。  
  
2.  在快捷菜单上，选择**“使用设计器编辑数据集”**。  
  
     NorthwindDataset 在**“数据集设计器”**中打开。  
  
## 向 CustomersTableAdapter 中添加第二个查询  
 该向导使用**“Customers”**数据表和**“CustomersTableAdapter”**创建数据集。  本节演练可将第二个查询添加到**“CustomersTableAdapter”**中。  
  
#### 将查询添加到 CustomersTableAdapter 中  
  
1.  将一个**“查询”**从**“工具箱”**的**“数据集”**选项卡拖到**“Customers”**表上。  
  
     将打开[TableAdapter 查询配置向导](../data-tools/editing-tableadapters.md)。  
  
2.  选择**“使用 SQL 语句”**，然后单击**“下一步”**。  
  
3.  选择**“选择（返回行）”**，然后单击**“下一步”**。  
  
4.  将 WHERE 子句添加到查询，结果为：  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  如果使用的是 Access 版的 Northwind，则将 @City 参数替换为问号。  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  在**“选择要生成的方法”**页面上，将**“填充 DataTable”**方法命名为 `FillByCity`。  
  
    > [!NOTE]
    >  本演练中未使用**“返回 DataTable”**方法，因此可以清除该复选框或保留默认名称。  
  
6.  单击**“下一步”**并完成该向导。  
  
     **FillByCity** 查询即会添加到 **CustomersTableAdapter**。  
  
## 在窗体上添加执行其他查询的代码  
  
#### 执行查询  
  
1.  在**“解决方案资源管理器”**中选择**“Form1”**，然后单击**“视图设计器”**。  
  
2.  将**“Customers”**节点从**“数据源”**窗口拖到**“Form1”**上。  
  
3.  通过从**“视图”**菜单选择**“代码”**更改为代码视图。  
  
4.  将 `Form1_Load` 事件处理程序中的代码替换为以下运行 `FillByCity` 查询的代码。  
  
     [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
## 运行应用程序  
  
#### 运行应用程序  
  
-   按 F5。  
  
-   网格将由 `City` 值为 `Seattle` 的客户进行填充。  
  
## 后续步骤  
  
### 将功能添加到你的应用程序  
  
-   添加一个 <xref:System.Windows.Forms.TextBox> 控件和 <xref:System.Windows.Forms.Button> 控件，并将文本框中的值传递给查询。  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\).  
  
-   将验证逻辑添加到该数据集中数据表的 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件中。  有关详细信息，请参阅[验证数据集中的数据](../data-tools/validate-data-in-datasets.md)。  
  
## 请参阅  
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)   
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)