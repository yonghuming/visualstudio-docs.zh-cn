---
title: "演练：文档级项目中的复杂数据绑定"
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
  - "复杂数据 [Visual Studio 中的 Office 开发]"
  - "数据 [Visual Studio 中的 Office 开发], 绑定数据"
  - "数据绑定 [Visual Studio 中的 Office 开发], 多个列"
  - "多列数据绑定 [Visual Studio 中的 Office 开发]"
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 演练：文档级项目中的复杂数据绑定
  本演练演示文档级项目中复杂数据绑定的基础知识。  可以将 Microsoft Office Excel 工作表中的多个单元格绑定到 Northwind SQL Server 数据库中的字段。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   将数据源添加到工作簿项目。  
  
-   将数据绑定控件添加到工作表。  
  
-   将数据更改保存回数据库。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   访问带有 Northwind SQL Server 示例数据库的服务器。  
  
-   从 SQL Server 数据库中读取数据和向其中写入数据的权限。  
  
## 创建新项目  
 第一步是要创建一个 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  创建一个名为 **My Complex Data Binding** 的 Excel 工作簿项目。  在向导中，选择**“创建新文档”**。  
  
     有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 在设计器中打开新的 Excel 工作簿并将“My Complex Data Binding”项目添加到**“解决方案资源管理器”**中。  
  
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
  
8.  选择**“Employees”**表旁边的复选框。  
  
9. 单击“完成”。  
  
 向导将**“Employees”**表添加到**“数据源”**窗口中。  还将一个类型化数据集添加到在**“解决方案资源管理器”**中可见的项目中。  
  
## 将控件添加到工作表  
 打开工作簿时，一个工作表会显示**“Employees”**表。  用户将能够更改数据，然后通过单击某个按钮将这些更改保存回数据库。  
  
 若要将工作表自动绑定到表，可以从**“数据源”**窗口将一个 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件绑定到工作表。  若要为用户提供保存更改的选项，可以从**“工具箱”**添加一个 <xref:System.Windows.Forms.Button> 控件。  
  
#### 添加列表对象  
  
1.  验证 **My Complex Data Binding.xlsx** 工作簿在 Visual Studio 中打开设计器，与 **Sheet1** 中显示。  
  
2.  打开**“数据源”**窗口，然后选择**“Employees”**节点。  
  
3.  单击出现的下拉箭头。  
  
4.  在下拉列表中选择**“ListObject”**。  
  
5.  将**“Employees”**表拖到单元格**“A6”**。  
  
     将在单元格**“A6”**中创建一个名为 `EmployeesListObject` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  同时，会将一个名为 `EmployeesBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、一个表适配器和一个 <xref:System.Data.DataSet> 实例添加到该项目中。  该控件绑定到 <xref:System.Windows.Forms.BindingSource>，接着后者绑定到 <xref:System.Data.DataSet> 实例。  
  
#### 添加按钮  
  
1.  从**“工具箱”**的**“公共控件”**选项卡上，将 <xref:System.Windows.Forms.Button> 控件添加到工作表的单元格**“A4”**中。  
  
 下一步是在工作表打开时将文本添加到按钮中。  
  
## 初始化控件  
 在 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件处理程序中将文本添加到按钮中。  
  
#### 初始化控件  
  
1.  在**“解决方案资源管理器”**中右击**“Sheet1.vb”**或**“Sheet1.cs”**，再单击快捷菜单上的**“查看代码”**。  
  
2.  将以下代码添加到 `Sheet1_Startup` 方法中，以设置 b`utton` 的文本。  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#8)]  
  
3.  仅对于 C\#，向 `Sheet1_Startup` 方法添加 <xref:System.Windows.Forms.Control.Click> 事件的事件处理程序。  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#9)]  
  
 现在，请添加代码以处理按钮的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
## 将更改保存到数据库  
 对数据所做的所有更改仅存在于本地数据集中，直到将这些更改显式保存回数据库为止。  
  
#### 将更改保存到数据库  
  
1.  为 b`utton` 的 <xref:System.Windows.Forms.Control.Click> 事件添加一个事件处理程序，然后添加下面的代码以将在数据集中所做的所有更改都提交回数据库。  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#10)]  
  
## 测试应用程序  
 现在可以测试工作簿，以验证数据是否按预期方式显示，以及是否可以在列表对象中操作数据。  
  
#### 测试数据绑定  
  
-   按 F5。  
  
     验证工作簿打开时列表对象中是否填充了**“Employees”**表中的数据。  
  
#### 修改数据  
  
1.  单击单元格**“B7”**，该单元格应包含名称**“Davolio”**。  
  
2.  键入名称“Anderson”，然后按 Enter。  
  
#### 修改列标头  
  
1.  单击包含列标头**“LastName”**的单元格。  
  
2.  键入“Last Name”并在这两个单词之间加一个空格，然后按 Enter。  
  
#### 保存数据  
  
1.  在工作表上单击**“保存”**。  
  
2.  退出 Excel。  当提示保存所做的更改时，请单击**“否”**。  
  
3.  按“F5”再次运行项目。  
  
     列表对象中填充了**“Employees”**表中的数据。  
  
4.  请注意，单元格**“B7”**中的名称仍然为“Anderson”，此名称是已执行且已保存回数据库的数据更改。  列标头**“LastName”**已改回没有空格的原始格式，因为列标头没有绑定到数据库，并且您未将所做的更改保存到工作表。  
  
#### 添加新行  
  
1.  在列表对象内选择一个单元格。  
  
     新行显示在列表底部，且新行的第一个单元格中带有一个星号（**“\*”**）。  
  
2.  在空行中添加以下信息。  
  
    |EmployeeID|LastName|FirstName|标题|  
    |----------------|--------------|---------------|--------|  
    |10|Ito|Shu|Sales Manager|  
  
#### 删除行  
  
-   右击工作表最左侧的数字 16（行 16），然后单击**“删除”**。  
  
#### 对列表中的行进行排序  
  
1.  在列表内选择一个单元格。  
  
     箭头按钮将显示在每个列标头中。  
  
2.  单击**“Last Name”**列标头中的箭头按钮。  
  
3.  单击**“升序排序”**。  
  
     行随即按照姓氏以字母顺序进行排序。  
  
#### 筛选信息  
  
1.  在列表内选择一个单元格。  
  
2.  单击**“Title”**列标头中的箭头按钮。  
  
3.  单击**“Sales Representative”**。  
  
     该列表仅显示**“Title”**列为**“Sales Representative”**的行。  
  
4.  再次单击**“Title”**列标头中的箭头按钮。  
  
5.  单击**“\(全部\)”**。  
  
     筛选内容随即被移除，并显示所有行。  
  
## 后续步骤  
 本演练演示将数据库中的表绑定到列表对象的基本操作。  以下是接下来可能要执行的一些任务：  
  
-   缓存数据，以使其可以脱机使用。  有关更多信息，请参见[如何：缓存数据以便脱机使用或在服务器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   部署解决方案。  有关更多信息，请参见[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
-   在字段与表之间创建主\/从关系。  有关更多信息，请参见[演练：使用缓存的数据集创建主&#47;从关系](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [演练：文档级项目中的简单数据绑定](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  