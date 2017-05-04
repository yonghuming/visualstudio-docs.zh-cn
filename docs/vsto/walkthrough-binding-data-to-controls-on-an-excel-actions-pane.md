---
title: "演练：将数据绑定到 Excel 操作窗格上的控件 | Microsoft Docs"
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
  - "操作窗格 [Visual Studio 中的 Office 开发], 绑定控件"
  - "操作窗格 [Visual Studio 中的 Office 开发], 数据绑定"
  - "控件 [Visual Studio 中的 Office 开发], 数据绑定"
  - "数据绑定 [Visual Studio 中的 Office 开发], 操作窗格"
  - "数据绑定 [Visual Studio 中的 Office 开发], 智能文档"
  - "智能文档 [Visual Studio 中的 Office 开发], 数据绑定"
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# 演练：将数据绑定到 Excel 操作窗格上的控件
  此演练演示如何在 Microsoft Office Excel 中将数据绑定到操作窗格上的控件。  这些控件演示 SQL Server 数据库中的表之间的主\/从关系。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   将控件添加到工作表中。  
  
-   创建操作窗格控件。  
  
-   将数据绑定 Windows 窗体控件添加到操作窗格控件。  
  
-   打开应用程序时显示操作窗格。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   访问带有 Northwind SQL Server 示例数据库的服务器。  
  
-   从 SQL Server 数据库中读取数据和向其中写入数据的权限。  
  
## 创建项目  
 第一步是要创建一个 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  创建一个 Excel 工作簿项目，并将其命名为“我的 Excel 操作窗格”。  在向导中，选择**“创建新文档”**。  有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 在设计器中打开新的 Excel 工作簿并将**“我的 Excel 操作窗格”**项目添加到**“解决方案资源管理器”**中。  
  
## 向项目中添加新的数据源  
  
#### 向项目中添加新的数据源  
  
1.  如果 **数据源** 窗口不可见，则显示那么，在菜单栏上，选择 **查看**，**其他窗口**，**数据源**。  
  
2.  选择 **添加新数据源** 开始 **数据源配置向导**。  
  
3.  选择**“数据库”**，然后单击**“下一步”**。  
  
4.  选择到 Northwind 示例 SQL Server 数据库的数据连接，或者使用**“新建连接”**按钮添加新连接。  
  
5.  单击**“下一步”**。  
  
6.  如果选择了该选项，请将其清除以保存连接，然后单击**“下一步”**。  
  
7.  展开**“数据库对象”**窗口中的**“表”**节点。  
  
8.  选择**“Suppliers”**表旁边的复选框。  
  
9. 展开**“Products”**表，并选择**“ProductName”**、**“SupplierID”**、**“QuantityPerUnit”**和**“UnitPrice”**。  
  
10. 单击“完成”。  
  
 向导将**“Suppliers”**表和**“Products”**表添加到**“数据源”**窗口中。  还将一个类型化数据集添加到在**“解决方案资源管理器”**中可见的项目中。  
  
## 将控件添加到工作表  
 接下来，将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件和 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到第一个工作表中。  
  
#### 添加 NamedRange 控件和 ListObject 控件  
  
1.  验证 **My Excel Actions Pane.xlsx** 工作簿在 Visual Studio 中打开设计器，与 `Sheet1` 显示。  
  
2.  在**“数据源”**窗口中展开**“Suppliers”**表。  
  
3.  在**“Company Name”**节点上单击下拉箭头，然后单击**“NamedRange”**。  
  
4.  将**“Company Name”**从**“数据源”**窗口拖到 `Sheet1` 中的**“A2”**单元格中。  
  
     将创建一个名为 `CompanyNameNamedRange` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，并在**“A2”**单元格中出现文本 \<CompanyName\>。  同时，会将一个名为 `suppliersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、一个表适配器和一个 <xref:System.Data.DataSet> 添加到该项目中。  该控件绑定到 <xref:System.Windows.Forms.BindingSource>，接着后者绑定到 <xref:System.Data.DataSet> 实例。  
  
5.  在**“数据源”**窗口中，向下滚动通过**“Suppliers”**表下的列。  该列表的下面是**“Products”**表；它之所以位于此处是因为它是**“Suppliers”**表的子表。  选择此**“Products”**表（不是与**“Suppliers”**表位于同一层的那个），然后单击出现的下拉箭头。  
  
6.  单击下拉列表中的**“ListObject”**，然后将**“Products”**表拖到 `Sheet1` 的**“A6”**单元格中。  
  
     这将在**“A6”**单元格中创建一个名为 `ProductNameListObject` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  同时，会将一个名为 `productsBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 和一个表适配器添加到该项目中。  该控件绑定到 <xref:System.Windows.Forms.BindingSource>，接着后者绑定到 <xref:System.Data.DataSet> 实例。  
  
7.  仅对 C\# 来说，选择组件栏上的**“suppliersBindingSource”**，然后在**“属性”**窗口中将**“Modifiers”**属性更改为“Internal”。  
  
## 向操作窗格中添加控件  
 然后，您需要一个包含组合框的操作窗格控件。  
  
#### 添加操作窗格控件  
  
1.  在**“解决方案资源浏览器”**中选择**“我的 Excel 操作窗格”**。  
  
2.  在**“项目”**菜单上，单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中选择**“操作窗格控件”**，将其命名为 **ActionsControl**，然后单击**“添加”**。  
  
#### 将数据绑定 Windows 窗体控件添加到操作窗格控件  
  
1.  将 <xref:System.Windows.Forms.ComboBox> 控件从**“工具箱”**的**“公共控件”**选项卡拖动到操作窗格控件。  
  
2.  将**“Size”**属性更改为“171, 21”。  
  
3.  调整用户控件的大小，使其适合组合框。  
  
## 将操作窗格上的控件绑定到数据  
 在本节中，要将 <xref:System.Windows.Forms.ComboBox> 的数据源设置为与工作表上的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件相同的数据源。  
  
#### 设置控件的数据绑定属性  
  
1.  右击操作窗格控件，然后单击**“查看代码”**。  
  
2.  将以下代码添加到操作窗格控件的 <xref:System.Windows.Forms.UserControl.Load> 事件中。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ActionsControl.vb#1)]  
  
3.  在 C\# 中，必须为 `ActionsControl` 创建事件处理程序。  可以将此代码放在 `ActionsControl` 构造函数中。  有关创建事件处理程序的更多信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#2)]  
  
## 显示操作窗格  
 操作窗格将不可见，直至您在运行时添加控件为止。  
  
#### 显示操作窗格  
  
1.  在**“解决方案资源管理器”**中，右击 ThisWorkbook.vb 或 ThisWorkbook.cs，然后单击**“查看代码”**。  
  
2.  在 `ThisWorkbook` 类中创建用户控件的新实例。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#3)]  
  
3.  在 `ThisWorkbook` 的 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 事件处理程序中，将控件添加到操作窗格。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#4)]  
  
## 测试应用程序  
 现在可以对文档进行测试，以验证当文档打开时操作窗格是否打开，以及控件是否具有主\/从关系。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  确认操作窗格可见。  
  
3.  在列表框中选择一个公司。  验证 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件中是否列出了公司名称，并验证 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件中是否列出了产品详细信息。  
  
4.  选择不同的公司以验证是否对公司名称和产品详细信息进行了适当的更改。  
  
## 后续步骤  
 以下是接下来可能要执行的一些任务：  
  
-   将数据绑定到 Word 中的控件。  有关更多信息，请参见[演练：将数据绑定到“Word 操作”窗格上的控件](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
-   部署项目。  有关更多信息，请参见[使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## 请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [如何：管理操作窗格上的控件布局](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  