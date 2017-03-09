---
title: "演练：创建用于搜索数据的 Windows 窗体 | Microsoft Docs"
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
  - "数据 [Visual Studio], 参数化查询"
  - "数据 [Visual Studio], 搜索"
  - "参数, 显示已筛选的数据"
  - "Windows 窗体, 显示数据"
  - "Windows 窗体, 搜索数据"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建用于搜索数据的 Windows 窗体
一个常见的应用程序方案是显示窗体上选择的数据。  例如，你可能希望显示特定客户的订单或特定订单的详细信息。  在本方案中，用户向窗体输入信息，然后以用户的输入作为参数执行查询，即基于参数化查询来选择数据。  查询只返回符合用户输入的条件的数据。  本演练显示了如何创建返回特定城市中客户的查询，并修改用户界面，以便用户可以输入城市名称并按按钮以执行该查询。  
  
 通过让数据库执行其最擅长的工作（即快速筛选记录），使用参数化查询有助于使你的应用程序更有效。  相反，如果你请求整个数据库表、在网络上传输它，然后使用应用程序逻辑查找想要的记录，则应用程序将变慢且不实用。  
  
 可以使用 [“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) 将参数化查询添加到任何 TableAdapter（以及接受参数值和执行查询的控件）。  通过在**“数据”**菜单上（或任何 TableAdapter 智能标记上）选择**“添加查询”**命令来打开对话框。  
  
 本演练涉及以下任务：  
  
-   创建新的**“Windows 应用程序”**项目。  
  
-   使用[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)在应用程序中创建和配置数据源。  
  
-   在[“数据源”窗口](../Topic/Data%20Sources%20Window.md)中设置项的拖放类型。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   通过将项从**“数据源”**窗口拖动到窗体上来创建显示数据的控件。  
  
-   添加用于在窗体上显示数据的控件。  
  
-   完成[“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
-   将参数输入到窗体中并执行参数化查询。  
  
## 系统必备  
 若要完成本演练，你需要：  
  
-   能够访问 Northwind 示例数据库。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建 Windows 应用程序  
 第一步是创建**“Windows 应用程序”**。  在此步骤中为项目指定名称是可选的，但由于我们打算稍后保存该项目，因此为它指定了一个名称。  
  
#### 创建新的 Windows 应用程序项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  将该项目命名为 `WindowsSearchForm`。  
  
3.  选择**“Windows 应用程序”**，然后单击**“确定”**。  有关详细信息，请参阅[客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     **“WindowsSearchForm”**项目即被创建并添加到**“解决方案资源管理器”**中。  
  
## 创建数据源  
 此步骤使用**“数据源配置向导”**从数据库创建一个数据源。  你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。  有关设置 Northwind 示例数据库的信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
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
  
## 创建窗体  
 通过将某些项从**“数据源”**窗口拖到你的窗体上，可创建数据绑定控件。  
  
#### 在窗体上创建数据绑定控件  
  
1.  在**“数据源”**窗口中展开**“Customers”**节点。  
  
2.  将**“Customers”**节点从**“数据源”**窗口中拖到窗体上。  
  
     窗体上出现用于导航记录的 <xref:System.Windows.Forms.DataGridView> 和工具栏 \(<xref:System.Windows.Forms.BindingNavigator>\)。  组件栏中出现 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
## 将参数化功能（搜索功能）添加到查询  
 使用 [“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) 向原始查询添加一个 WHERE 子句。  
  
#### 创建参数化查询和用于输入参数的控件  
  
1.  选择 <xref:System.Windows.Forms.DataGridView> 控件，然后在**“数据”**菜单上选择**“添加查询”**。  
  
2.  在[“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)的**“新查询名称”**区域中键入 `FillByCity`。  
  
3.  将 `WHERE City = @City` 添加到**“查询文本”**区域的查询中。  
  
     查询应当类似于：  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Access 和 OleDb 数据源使用问号“?”表示参数，所以 WHERE 子句将类似于：`WHERE City = ?`。  
  
4.  单击**“确定”**以关闭**“查询标准生成器”**对话框。  
  
     **“FillByCityToolStrip”**即添加到窗体中。  
  
## 测试应用程序  
 运行应用程序以打开准备接收参数作为输入的窗体。  
  
#### 测试应用程序  
  
1.  按 F5 运行该应用程序。  
  
2.  在**“City”**文本框中键入“London”，然后单击**“FillByCity”**。  
  
     数据网格即用符合参数化条件的客户填充。  在此示例中，数据网格只显示其**“City”**列中有**“London”**值的客户。  
  
## 后续步骤  
 根据应用程序的要求，在创建参数化窗体后可能还需要执行一些步骤。  你可以通过以下操作来增强此演练的效果：  
  
-   添加显示相关数据的控件。  有关详细信息，请参阅[如何：在 Windows 窗体应用程序中显示相关数据](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)。  
  
-   编辑数据集来添加或移除数据库对象。  有关详细信息，请参阅[如何：编辑数据集](../Topic/How%20to:%20Edit%20a%20Dataset.md)。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [BindingSource 组件概述](../Topic/BindingSource%20Component%20Overview.md)   
 [BindingNavigator 控件概述](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)