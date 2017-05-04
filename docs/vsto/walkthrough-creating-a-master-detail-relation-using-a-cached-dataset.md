---
title: "演练：使用缓存的数据集创建主/从关系 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "数据缓存 [Visual Studio 中的 Office 开发], 主/从关系"
  - "主-从表 [Visual Studio 中的 Office 开发], 演练"
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 演练：使用缓存的数据集创建主/从关系
  本演练演示如何在工作表上创建主\/从关系，以及如何缓存数据，以使解决方案可以脱机使用。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 通过此演练，您将学会如何执行以下任务：  
  
-   将控件添加到工作表中。  
  
-   设置要在工作表中缓存的数据集。  
  
-   添加用于滚动记录的代码。  
  
-   测试项目。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   对 Northwind SQL Server 示例数据库的访问。  数据库可位于开发计算机上或服务器上。  
  
-   从 SQL Server 数据库中读取数据和向其中写入数据的权限。  
  
## 创建新项目  
 在此步骤中，您将创建一个 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  使用 Visual Basic 或 C\#，创建一个 Excel 工作簿项目并将其命名为**“My Master\-Detail”**。  确保已选择**“创建新文档”**。  有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 Visual Studio 在设计器中打开新的 Excel 工作簿，并将“My Master\-Detail”项目添加到**“解决方案资源管理器”**中。  
  
## 创建数据源  
 使用**“数据源”**窗口向您的项目中添加类型化数据集。  
  
#### 创建数据源  
  
1.  如果 **数据源** 窗口不可见，则显示那么，在菜单栏上，选择 **查看**，**其他窗口**，**数据源**。  
  
2.  选择 **添加新数据源** 开始 **数据源配置向导**。  
  
3.  选择**“数据库”**，然后单击**“下一步”**。  
  
4.  选择到 Northwind 示例 SQL Server 数据库的数据连接，或者使用**“新建连接”**按钮添加新连接。  
  
5.  选择或创建连接后，单击**“下一步”**。  
  
6.  如果选择了该选项，请将其清除以保存连接，然后单击**“下一步”**。  
  
7.  展开**“数据库对象”**窗口中的**“表”**节点。  
  
8.  选择**“Orders”**表，然后选择**“Order Details”**表。  
  
9. 单击“完成”。  
  
 向导将这两个表添加到**“数据源”**窗口中。  还将一个类型化数据集添加到在**“解决方案资源管理器”**中可见的项目中。  
  
## 将控件添加到工作表  
 在此步骤中，将在第一个工作表中添加一个命名范围、一个列表对象和两个按钮。  首先，从**“数据源”**窗口添加命名范围和列表对象，从而使其自动绑定至数据源。  然后，从**“工具箱”**添加按钮。  
  
#### 添加命名范围和列表对象  
  
1.  验证 **My Master\-Detail.xlsx** 工作簿在 Visual Studio 中打开设计器，与 **Sheet1** 中显示。  
  
2.  打开**“数据源”**窗口，然后展开**“Orders”**节点。  
  
3.  选择**“OrderID”**列，然后单击出现的下拉箭头。  
  
4.  单击下拉列表中的**“NamedRange”**，然后将**“OrderID”**列拖至单元格**“A2”**中。  
  
     将在单元格**“A2”**中创建一个名为 `OrderIDNamedRange` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  同时，会将一个名为 `OrdersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、一个表适配器和一个 <xref:System.Data.DataSet> 实例添加到该项目中。  该控件绑定到 <xref:System.Windows.Forms.BindingSource>，接着后者绑定到 <xref:System.Data.DataSet> 实例。  
  
5.  向下滚动通过**“Orders”**表下的列。  该列表的底部是**“Order Details”**表；该表位于此处是因为它是**“Orders”**表的子表。  选择这个**“Order Details”**表，而不是与**“Orders”**表处于同一层的某个表，然后单击出现的下拉箭头。  
  
6.  单击下拉列表中的**“ListObject”**，然后将**“Order Details”**表拖至单元格**“A6”**中。  
  
7.  将在单元格**“A6”**中创建一个名为**“Order\_DetailsListObject”**的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件，并将其绑定到 <xref:System.Windows.Forms.BindingSource>。  
  
#### 添加两个按钮  
  
1.  从**“工具箱”**的**“公共控件”**选项卡向工作表的单元格**“A3”**中添加一个 <xref:System.Windows.Forms.Button> 控件。  
  
     此按钮被命名为 `Button1`。  
  
2.  将另一个 <xref:System.Windows.Forms.Button> 控件添加到工作表的单元格**“B3”**中。  
  
     此按钮被命名为 `Button2`。  
  
 接下来，标记将在文档中缓存的数据集。  
  
## 缓存数据集  
 通过将数据集设置为 public 并设置**“CacheInDocument”**属性，可标记要在文档中缓存的数据集。  
  
#### 缓存数据集  
  
1.  在组件栏中选择**“NorthwindDataSet”**。  
  
2.  在**“属性”**窗口中，将**“Modifiers”**属性更改为**“Public”**。  
  
     启用缓存之前，必须将数据集设置为 public。  
  
3.  将**“CacheInDocument”**属性更改为**“True”**。  
  
 下一步是向按钮中添加文本，并在 C\# 中添加用于将事件处理程序挂钩的代码。  
  
## 初始化控件  
 在处理 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 事件期间，设置按钮文本并添加事件处理程序。  
  
#### 初始化数据和控件  
  
1.  在**“解决方案资源管理器”**中右击**“Sheet1.vb”**或**“Sheet1.cs”**，再单击快捷菜单上的**“查看代码”**。  
  
2.  将以下代码添加到 `Sheet1_Startup` 方法中，以设置按钮文本。  
  
     [!code-csharp[Trin_VstcoreDataExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#15)]
     [!code-vb[Trin_VstcoreDataExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#15)]  
  
3.  仅对于 C\#，向 `Sheet1_Startup` 方法添加用于处理按钮单击事件的事件处理程序。  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#16)]  
  
## 添加用于滚动记录的代码  
 在每个按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中添加代码以在记录中移动。  
  
#### 滚动记录  
  
1.  为 `Button1` 的 <xref:System.Windows.Forms.Control.Click> 事件添加事件处理程序，并添加以下代码以在记录中向后移动：  
  
     [!code-csharp[Trin_VstcoreDataExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#17)]
     [!code-vb[Trin_VstcoreDataExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#17)]  
  
2.  为 `Button2` 的 <xref:System.Windows.Forms.Control.Click> 事件添加事件处理程序，并添加以下代码以在记录中向前移动：  
  
     [!code-csharp[Trin_VstcoreDataExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#18)]
     [!code-vb[Trin_VstcoreDataExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#18)]  
  
## 测试应用程序  
 现在您可以测试工作簿，以确保数据按预期效果显示，并且可以脱机使用该解决方案。  
  
#### 测试数据缓存  
  
1.  按 F5。  
  
2.  验证命名范围和列表对象是否被来自数据源的数据所填充。  
  
3.  通过单击按钮，滚动一些记录。  
  
4.  保存工作簿，然后关闭工作簿和 Visual Studio。  
  
5.  禁用到数据库的连接。  如果数据库位于服务器上，则拔掉计算机的网线，或者如果数据库位于开发计算机上，则停止 SQL Server 服务。  
  
6.  打开 Excel 然后打开 **My Master\-Detail.xlsx** 从 \\bin 目录 \(\\my master\-detail\\bin 在 Visual Basic 或 \\my master\-detail\\bin\\debug 在 c\# 中\)。  
  
7.  滚动一些记录，以查看断开连接后工作表是否操作正常。  
  
8.  重新连接数据库。  如果数据库位于服务器上，则将计算机再次连接到网络，或者如果数据库位于开发计算机上，则启动 SQL Server 服务。  
  
## 后续步骤  
 本演练演示在工作表上创建主\/从数据关系及缓存数据集的基本操作。  以下是接下来可能要执行的一些任务：  
  
-   部署解决方案。  有关更多信息，请参阅[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [缓存数据](../vsto/caching-data.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
  