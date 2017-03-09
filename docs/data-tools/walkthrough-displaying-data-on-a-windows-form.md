---
title: "演练：在 Windows 窗体上显示数据 | Microsoft Docs"
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
  - "数据 [Visual Studio], 在 Windows 窗体上显示"
  - "数据绑定, Windows 窗体"
  - "在窗体上显示数据, 演练"
  - "窗体, 显示数据"
  - "Windows 应用程序, 显示数据"
  - "Windows 窗体, 显示数据"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 演练：在 Windows 窗体上显示数据
在应用程序开发中最常用的方案之一是在基于 Windows 的应用程序中的窗体上显示数据。  通过将项从[“数据源”窗口](../Topic/Data%20Sources%20Window.md)拖到窗体上，可在窗体上显示数据。  本演练将创建一个简单窗体，用于在几个单独的控件中显示单个表的数据。  本示例使用源自 Northwind 示例数据库的 `Customers` 表。  
  
 本演练涉及以下任务：  
  
-   创建新的**“Windows 应用程序”**项目。  
  
-   使用[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)创建并配置数据集。  
  
-   选择从**“数据源”**窗口拖动某些项时要在窗体上创建的控件。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   通过将项从**“数据源”**拖到你的窗体上来创建数据绑定控件。  
  
## 系统必备  
 若要完成本演练，你需要：  
  
-   能够访问 Northwind 示例数据库。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建 Windows 应用程序  
 第一步是创建**“Windows 应用程序”**项目。  
  
#### 创建新的 Windows 应用程序项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  将项目命名为 `DisplayingDataonaWindowsForm`。  
  
3.  选择**“Windows 应用程序”**，然后单击**“确定”**。  有关详细信息，请参阅[客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     **“DisplayingDataonaWindowsForm”**项目即被创建并添加到**“解决方案资源管理器”**中。  
  
## 创建数据源  
 此步骤基于 Northwind 示例数据库中 `Customers` 表使用**“数据源配置向导”**创建数据源。  你必须具有对 Northwind 示例数据库的访问权限，才能创建连接。  有关设置 Northwind 示例数据库的信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
#### 创建数据源  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
2.  在**“数据源”**窗口中，选择**“添加新数据源”**以启动**“数据源配置向导”**。  
  
3.  在**“选择数据源类型”**页上选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择你的数据连接”**页面上，执行以下操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
         \- 或 \-  
  
    -   选择**“新建连接”**以启动**“添加\/修改连接”**对话框。  
  
5.  如果数据库需要密码，请选择该选项以包括敏感数据，再单击**“下一步”**。  
  
6.  在**“将连接字符串保存到应用程序配置文件”**页面上单击**“下一步”**。  
  
7.  在**“选择数据库对象”**页面上展开**“表”**节点。  
  
8.  选择**“Customers”**表，然后单击**“完成”**。  
  
     **“NorthwindDataSet”**即被添加到你的项目中，并且**“数据源”**窗口中将显示**“Customers”**表。  
  
## 设置要创建的控件  
 对于本演练，数据将采用**“详细信息”**布局（数据在单独控件中显示）。  （替代方法是默认的**“网格”**布局，该布局中的数据显示在 <xref:System.Windows.Forms.DataGridView> 控件中。）  
  
#### 设置“数据源”窗口中项的拖放类型  
  
1.  在**“数据源”**窗口中展开**“Customers”**节点。  
  
2.  通过从**“Customers”**节点上的下拉列表中选择**“详细信息”**，将**“Customers”**表的拖放类型更改为**“详细信息”**。  有关详细信息，请参阅[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
3.  通过从**“CustomerID”**节点上的控件列表中选择**“标签”**，将**“CustomerID”**列的拖放类型更改为标签。  
  
## 创建窗体  
 通过将某些项从**“数据源”**窗口拖到你的窗体上来创建数据绑定控件。  
  
#### 在窗体上创建数据绑定控件  
  
-   将主**“Customers”**节点从**“数据源”**窗口拖到窗体上。  
  
     带有描述性标签的数据绑定控件将显示在窗体上，同时还显示一个工具条 \(<xref:System.Windows.Forms.BindingNavigator>\)，用于在记录间进行导航。  组件栏中出现 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
## 测试应用程序  
  
#### 运行应用程序  
  
-   按 F5。  
  
-   使用 <xref:System.Windows.Forms.BindingNavigator> 控件导航记录。  
  
## 后续步骤  
 根据应用程序的要求，在创建了绑定数据的 Windows 窗体后，还需要执行一些步骤。  你可以通过以下操作来增强此演练的效果：  
  
-   将搜索功能添加到该窗体。  有关详细信息，请参阅[如何：向 Windows 窗体应用程序中添加参数化查询](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)。  
  
-   添加将更新发送回数据库的功能。  有关详细信息，请参阅[演练：将数据保存到数据库（单个表）](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md)。  
  
-   通过从**“数据源”**窗口中选择**“使用向导配置数据集”**，将 `Orders` 表添加到数据集中。  然后，通过将**“Orders”**节点（位于**“Customers”**表中**“Fax”**列下面的一个节点）拖到窗体上，可添加显示相关数据的控件。  有关详细信息，请参阅[如何：在 Windows 窗体应用程序中显示相关数据](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)