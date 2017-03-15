---
title: "演练：使用数据集设计器创建数据集 | Microsoft Docs"
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
  - "数据 [Visual Studio], 数据集设计器"
  - "数据集设计器, 演练"
  - "数据集 [Visual Basic], 创建"
  - "数据集 [Visual Basic], 演练"
  - "XML 架构, 创建数据集"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 演练：使用数据集设计器创建数据集
在此演练中，您将使用**“数据集设计器”**创建数据集。  它将指导您完成创建新项目并向其中添加新**“数据集”**项的全过程。  您将学会在不使用向导的情况下如何根据数据库中的表来创建表。  
  
 本演练涉及以下任务：  
  
-   创建新的**“Windows 应用程序”**项目。  
  
-   将空的**“数据集”**项添加到项目中。  
  
-   在应用程序中通过使用**“数据集设计器”**生成数据集来创建和配置数据源。  
  
-   在**“服务器资源管理器”**中创建到 Northwind 数据库的连接。  
  
-   根据数据库中的表在数据集中随 TableAdapter 一起创建表。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 系统必备  
 若要完成本演练，您需要：  
  
-   访问 Northwind 示例数据库（SQL Server 或 Access 版）。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
## 创建新的“Windows 应用程序”项目  
  
#### 创建新的 Windows 应用程序项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  在**“项目类型”**窗格中选择一种编程语言。  
  
3.  在**“模板”**窗格中单击**“Windows 应用程序”**。  
  
4.  将项目命名为 `DatasetDesignerWalkthrough`，然后单击**“确定”**。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会将该项目添加到**“解决方案资源管理器”**中，并在设计器中显示一个新窗体。  
  
## 将新的数据集添加到应用程序中  
  
#### 向项目添加新的数据集项  
  
1.  在**“项目”**菜单上，单击**“添加新项”**。  
  
     此时将显示**“添加新项”**对话框。  
  
2.  在**“添加新项”**对话框的**“模板”**框中，单击**“数据集”**。  
  
3.  将该数据集命名为 `NorthwindDataset`，然后单击**“添加”**。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会将名为**“NorthwindDataset.xsd”**的文件添加到项目，并在**“数据集设计器”**中打开该文件。  
  
## 在“服务器资源管理器”中创建数据连接  
  
#### 创建到 Northwind 数据库的连接  
  
1.  在**“视图”**菜单上，单击**“服务器资源管理器”**。  
  
2.  在**“服务器资源管理器”**中单击**“连接到数据库”**按钮。  
  
3.  创建到 Northwind 示例数据库的连接。  
  
    > [!NOTE]
    >  对于此演练，您可以连接到 Northwind 的 SQL Server 或 Access 版本。  
  
## 在数据集内创建表  
 本节将说明如何向数据集中添加表。  
  
#### 创建 Customers 表  
  
1.  在**“服务器资源管理器”**中展开您创建的数据连接，然后展开**“表”**节点。  
  
2.  将**“Customers”**表从**“服务器资源管理器”**中拖动到**“数据集设计器”**上。  
  
     **“Customers”**数据表和**“CustomersTableAdapter”**被添加到数据集中。  
  
#### 创建 Orders 表  
  
-   将**“Orders”**表从**“服务器资源管理器”**中拖动到**“数据集设计器”**上。  
  
     **“Orders”**数据表、**“OrdersTableAdapter”**以及**“Customers”**表与**“Orders”**表之间的数据关系将添加到数据集中。  
  
#### 创建 OrderDetails 表  
  
-   将**“Order Details”**表从**“服务器资源管理器”**拖动到**“数据集设计器”**上。  
  
     **“Order Details”**数据表、**“Order DetailsTableAdapter”**以及**“Orders”**表与**“Order Details”**表之间的数据关系将添加到数据集中。  
  
## 后续步骤  
  
### 在应用程序中添加功能  
  
-   保存数据集。  
  
-   在**“数据源”**窗口中选择项并将其拖动到一个窗体上。  有关详细信息，请参阅[在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
-   向 TableAdapter 中添加更多查询。  有关详细信息，请参阅[如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)。  
  
-   在该数据集中的数据表的 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件中添加验证逻辑。  有关详细信息，请参阅[验证数据集中的数据](../data-tools/validate-data-in-datasets.md)。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)