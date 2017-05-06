---
title: "演练：文档级项目中的简单数据绑定"
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
  - "数据 [Visual Studio 中的 Office 开发], 绑定数据"
  - "数据绑定 [Visual Studio 中的 Office 开发], 工作表单元格到数据库字段"
  - "数据库字段 [Visual Studio 中的 Office 开发]"
  - "简单数据绑定 [Visual Studio 中的 Office 开发]"
  - "工作表 [Visual Studio 中的 Office 开发], 将工作表单元格绑定到数据库字段"
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# 演练：文档级项目中的简单数据绑定
  此演练演示文档级项目中的数据绑定的基础知识。  将 SQL Server 数据库中的单个数据字段绑定到 Microsoft Office Excel 中的命名区域。  此演练还演示如何添加控件，让您能够滚动查看表中的所有记录。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   为 Excel 项目创建数据源。  
  
-   将控件添加到工作表中。  
  
-   滚动查看数据库记录。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   访问带有 Northwind SQL Server 示例数据库的服务器。  
  
-   从 SQL Server 数据库中读取数据和向其中写入数据的权限。  
  
## 创建新项目  
 在此步骤中，您将创建一个 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  使用 Visual Basic 或 C\# 创建一个名为 **My Simple Data Binding**的 Excel 工作簿项目。  确保已选择**“创建新文档”**。  有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 Visual Studio 在设计器中打开新的 Excel 工作簿并将“My Simple Data Binding”项目添加到**“解决方案资源管理器”**中。  
  
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
  
8.  选择**“Customers”**表旁边的复选框。  
  
9. 单击“完成”。  
  
 向导将**“Customers”**表添加到**“数据源”**窗口。  还将一个类型化数据集添加到在**“解决方案资源管理器”**中可见的项目中。  
  
## 将控件添加到工作表  
 对于此演练，第一个工作表上需要两个命名范围和四个按钮。  首先，从**“数据源”**窗口添加两个命名范围，这样它们就会自动绑定到数据源。  然后，从**“工具箱”**添加按钮。  
  
#### 添加两个命名范围  
  
1.  验证 **My Simple Data Binding.xlsx** 工作簿在 Visual Studio 中打开设计器，与 **Sheet1** 中显示。  
  
2.  打开**“数据源”**窗口并展开**“Customers”**节点。  
  
3.  选择**“CompanyName”**列，然后单击出现的下拉箭头。  
  
4.  在下拉列表中选择**“NamedRange”**，然后将**“CompanyName”**列拖动到单元格**“A1”**。  
  
     在单元格**“A1”**中会创建一个名为 `companyNameNamedRange` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  同时，会将一个名为 `customersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、一个表适配器和一个 <xref:System.Data.DataSet> 实例添加到该项目中。  该控件绑定到 <xref:System.Windows.Forms.BindingSource>，接着后者绑定到 <xref:System.Data.DataSet> 实例。  
  
5.  在**“数据源”**窗口中选择**“CustomerID”**列，然后单击出现的下拉箭头。  
  
6.  在下拉列表中单击**“NamedRange”**，然后将**“CustomerID”**列拖动到单元格**“B1”**。  
  
7.  另一个名为 `customerIDNamedRange` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件会在单元格**“B1”**中创建，并且该控件绑定到 <xref:System.Windows.Forms.BindingSource>。  
  
#### 添加四个按钮  
  
1.  从**“工具箱”**的**“公共控件”**选项卡向工作表的单元格**“A3”**中添加一个 <xref:System.Windows.Forms.Button> 控件。  
  
     此按钮被命名为 `Button1`。  
  
2.  按照此顺序在下列单元格中再添加三个按钮，使其名称如下所示：  
  
    |单元格|\(名称\)|  
    |---------|------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 下一步向按钮添加文本，并在 C\# 中添加事件处理程序。  
  
## 初始化控件  
 设置按钮文本并添加 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件期间的事件处理程序。  
  
#### 初始化控件  
  
1.  在**“解决方案资源管理器”**中右击**“Sheet1.vb”**或**“Sheet1.cs”**，再单击快捷菜单上的**“查看代码”**。  
  
2.  向 `Sheet1_Startup` 方法添加以下代码，从而为每个按钮设置文本。  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#2)]  
  
3.  仅对于 C\#，向 `Sheet1_Startup` 方法添加用于处理按钮单击事件的事件处理程序。  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#3)]  
  
 现在添加代码以处理按钮的 <xref:System.Windows.Forms.Control.Click> 事件，以便用户可以浏览记录。  
  
## 添加用于滚动记录的代码  
 在每个按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中添加代码以在记录中移动。  
  
#### 移动到第一条记录  
  
1.  添加 `Button1` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件的事件处理程序，并添加以下代码以移动到第一条记录：  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#4)]  
  
#### 移动到上一条记录  
  
1.  添加 `Button2` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件的事件处理程序，并添加以下代码以后退一个位置：  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#5)]  
  
#### 移动到下一条记录  
  
1.  添加 `Button3` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件的事件处理程序，并添加以下代码以前进一个位置：  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#6)]  
  
#### 移动到最后一条记录  
  
1.  添加 `Button4` 的 <xref:System.Windows.Forms.Control.Click> 事件的事件处理程序，并添加以下代码以移动到最后一条记录：  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#7)]  
  
## 测试应用程序  
 现在可以对工作簿进行测试，以确保能浏览数据库中的记录。  
  
#### 测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  确认第一条记录显示在单元格**“A1”**和**“B1”**中。  
  
3.  单击**“\>”**\(`Button3`\) 按钮，然后确认下一条记录出现在单元格**“A1”**和**“B1”**中。  
  
4.  单击其他滚动按钮以确认记录按预期发生变化。  
  
## 后续步骤  
 此演练演示将命名范围绑定到数据库中的字段的基本操作。  以下是接下来可能要执行的一些任务：  
  
-   缓存数据，以使其可以脱机使用。  有关更多信息，请参见[如何：缓存数据以便脱机使用或在服务器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   将单元格绑定到表中的多个列，而不是绑定到一个字段。  有关更多信息，请参见[演练：文档级项目中的复杂数据绑定](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)。  
  
-   使用 <xref:System.Windows.Forms.BindingNavigator> 控件滚动记录。  有关更多信息，请参见[如何：使用 Windows 窗体 BindingNavigator 控件定位数据](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [演练：文档级项目中的复杂数据绑定](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  