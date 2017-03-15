---
title: "演练：在 Windows 窗体间传递数据 | Microsoft Docs"
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
  - "数据 [Visual Studio], 在窗体之间传递"
  - "窗体, 传递数据于"
  - "演练 [Visual Studio], 数据"
  - "演练 [Windows 窗体], 数据"
  - "Windows 窗体, 演练"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：在 Windows 窗体间传递数据
本演练提供了有关将数据从一个窗体传递到另一个窗体的分步说明。  通过使用来自 Northwind 的客户和订单表，一个窗体将允许用户选择客户，而另一个窗体将显示所选择客户的订单。  本演练演示如何在窗体上创建从第一个窗体接收数据的方法。  
  
> [!NOTE]
>  本演练仅演示在窗体之间传递数据的一种方法。  向窗体传递数据还可以有其他选择，包括以下方法：创建另一个构造函数来接收数据，或者创建一个可用第一个窗体的数据进行设置的公共属性。  
  
 本演练涉及以下任务：  
  
-   创建新的**“Windows 应用程序”**项目。  
  
-   使用[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)创建并配置数据集。  
  
-   选择从**“数据源”**窗口拖动某些项时要在窗体上创建的控件。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   通过将某些项从**“数据源”**窗口拖到窗体上来创建数据绑定控件。  
  
-   创建具有网格的第二个窗体来显示数据。  
  
-   创建一个 TableAdapter 查询来获取特定客户的订单。  
  
-   在窗体间传递数据。  
  
## 系统必备  
 若要完成本演练，你需要：  
  
-   能够访问 Northwind 示例数据库。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建 Windows 应用程序  
  
#### 创建新的 Windows 项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  将项目命名为 `PassingDataBetweenForms`。  
  
3.  选择**“Windows 窗体应用程序”**，然后单击**“确定”**。  有关详细信息，请参阅[客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     **“PassingDataBetweenForms”**项目即被创建并添加到**“解决方案资源管理器”**中。  
  
## 创建数据源  
  
#### 创建数据源  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
2.  在**“数据源”**窗口中，选择**“添加新数据源”**以启动**“数据源配置向导”**。  
  
3.  在**“选择数据源类型”**页上选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择数据库模型”**页面上，确认已指定**“数据集”**，然后单击**“下一步”**。  
  
5.  在**“选择数据连接”**页面上，执行以下操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         \- 或 \-  
  
    -   选择**“新建连接”**，以启动**“添加\/修改连接”**对话框。  
  
6.  如果数据库需要密码并且已启用用于包括敏感数据的选项，请选择该选项，然后单击**“下一步”**。  
  
7.  在**“将连接字符串保存到应用程序配置文件”**页面上单击**“下一步”**。  
  
8.  在**“选择数据库对象”**页面上展开**“表”**节点。  
  
9. 选择**“Customers”**和**“Orders”**表，然后单击**“完成”**。  
  
     **“NorthwindDataSet”**将会添加到你的项目中，并且在**“数据源”**窗口中将显示**“Customers”**和“Orders”表。  
  
## 创建第一个窗体 \(Form1\)  
 通过将**“Customers”**节点从**“数据源”**窗口拖到窗体上，可以创建数据绑定网格（<xref:System.Windows.Forms.DataGridView> 控件）。  
  
#### 在窗体上创建数据绑定网格  
  
-   将主**“Customers”**节点从**“数据源”**窗口拖到**“Form1”**上。  
  
     在**“Form1”**上出现用于导航记录的 <xref:System.Windows.Forms.DataGridView> 和工具栏 \(<xref:System.Windows.Forms.BindingNavigator>\)。  组件栏中出现 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
## 创建第二个窗体 \(Form2\)  
  
#### 创建要传入数据的第二个窗体  
  
1.  从**“项目”**菜单中，选择**“添加 Windows 窗体”**。  
  
2.  保留**“Form2”**的默认名称，然后单击**“添加”**。  
  
3.  将主**“Orders”**节点从**“数据源”**窗口拖到**“Form2”**上。  
  
     在**“Form2”**上出现用于导航记录的 <xref:System.Windows.Forms.DataGridView> 和工具栏 \(<xref:System.Windows.Forms.BindingNavigator>\)。  组件栏中出现 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
4.  从组件栏中删除**“OrdersBindingNavigator”**。  
  
     **“OrdersBindingNavigator”**从**“Form2”**中消失。  
  
## 向 Form2 添加 TableAdapter 查询来为 Form1 上所选择的客户加载订单  
  
#### 创建 TableAdapter 查询  
  
1.  在**“解决方案资源管理器”**中双击**“NorthwindDataSet.xsd”**文件。  
  
2.  右键单击**“OrdersTableAdapter”**，然后选择**“添加查询”**。  
  
3.  保留**“使用 SQL 语句”**的默认选项，然后单击**“下一步”**。  
  
4.  保留**“选择\(返回行\)”**的默认选项，然后单击**“下一步”**。  
  
5.  向查询添加 WHERE 子句来根据 `CustomerID` 返回 `Orders`。  查询应当类似于：  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  验证数据库的参数语法是否正确。  例如，在 Microsoft Access 中，WHERE 子句应当如下：`WHERE CustomerID = ?`。  
  
6.  单击**“下一步”**。  
  
7.  对于**“填充 DataTable”**\-\>**“方法名称”**，键入`“FillByCustomerID”`。  
  
8.  清除**“返回 DataTable”**选项，然后单击**“下一步”**。  
  
9. 单击**“完成”**。  
  
## 在 Form2 上创建要传入数据的方法  
  
#### 创建要传入数据的方法  
  
1.  右键单击**“Form2”**，然后选择**“查看代码”**，以在**“代码编辑器”**中打开**“Form2”**。  
  
2.  将以下代码添加到 `Form2_Load` 方法后面的**“Form2”**：  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## 在 Form1 上创建用于传递数据并显示 Form2 的方法  
  
#### 创建向 Form2 传递数据的方法  
  
1.  在**“Form1”**中，右键单击“Customer”数据网格，然后单击**“属性”**。  
  
2.  在**“属性”**窗口中，单击**“事件”**。  
  
3.  双击**“CellDoubleClick”**事件。  
  
     将显示代码编辑器。  
  
4.  更新方法定义以匹配以下示例：  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## 运行应用程序  
  
#### 运行应用程序  
  
-   按 F5 运行该应用程序。  
  
-   在**“Form1”**中双击一个客户记录以打开包含该客户的订单的**“Form2”**。  
  
## 后续步骤  
 根据应用程序的要求，在窗体间传递数据之后可能还需要执行一些步骤。  你可以通过以下操作来增强此演练的效果：  
  
-   编辑数据集，以添加或移除数据库对象。  有关详细信息，请参阅[如何：编辑数据集](../Topic/How%20to:%20Edit%20a%20Dataset.md)。  
  
-   添加将数据保存回数据库的功能。  有关详细信息，请参阅[如何：将数据集更改保存到数据库中](../Topic/How%20to:%20Save%20Dataset%20Changes%20to%20a%20Database.md)。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)