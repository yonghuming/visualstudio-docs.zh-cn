---
title: "演练：将数据绑定到“Word 操作”窗格上的控件"
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
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# 演练：将数据绑定到“Word 操作”窗格上的控件
  此演练演示如何在一个绑定到操作窗格上的控件的数据在 Word。  这些控件演示 SQL Server 数据库中的表之间的主\/从关系。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   使用绑定到数据的 Windows 窗体控件来创建操作窗格。  
  
-   使用主\/从关系在控件中显示数据。  
  
-   在打开应用程序时显示操作窗格。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   访问带有 Northwind SQL Server 示例数据库的服务器。  
  
-   从 SQL Server 数据库中读取数据和向其中写入数据的权限。  
  
## 创建项目  
 第一步是创建 Word 文档项目。  
  
#### 创建新项目  
  
1.  创建一个名为“我的 Word 操作窗格”的 Word 文档项目。  在向导中，选择**“创建新文档”**。  
  
     有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 会在设计器中打开新的 Word 文档，并将**“我的 Word 操作窗格”**项目添加到**“解决方案资源管理器”**中。  
  
## 向操作窗格中添加控件  
 在此演练中，需要一个包含数据绑定 Windows 窗体控件的操作窗格控件。  向项目中添加一个数据源，然后将控件从**“数据源”**窗口拖动到操作窗格控件中。  
  
#### 添加操作窗格控件  
  
1.  在**“解决方案资源管理器”**中选择**“我的 Word 操作窗格”**项目。  
  
2.  在**“项目”**菜单上，单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中选择**“操作窗格控件”**，将它命名为**“ActionsControl”**，然后单击**“添加”**。  
  
#### 向项目添加数据源  
  
1.  如果 **数据源** 窗口不可见，则显示那么，在菜单栏上，选择 **查看**，**其他窗口**，**数据源**。  
  
    > [!NOTE]  
    >  如果**“显示数据源”**不可用，请单击 Word 文档，然后再次进行检查。  
  
2.  单击**“添加新数据源”**以启动**“数据源配置向导”**。  
  
3.  选择**“数据库”**，然后单击**“下一步”**。  
  
4.  选择到 Northwind 示例 SQL Server 数据库的数据连接，或者使用**“新建连接”**按钮添加新连接。  
  
5.  单击**“下一步”**。  
  
6.  如果选择了该选项，请将其清除以保存连接，然后单击**“下一步”**。  
  
7.  展开**“数据库对象”**窗口中的**“表”**节点。  
  
8.  选择**“Suppliers”**表和**“Products”**表旁边的复选框。  
  
9. 单击“完成”。  
  
 向导将**“Suppliers”**表和**“Products”**表添加到**“数据源”**窗口中。  还将一个类型化数据集添加到在**“解决方案资源管理器”**中可见的项目中。  
  
#### 将数据绑定 Windows 窗体控件添加到操作窗格控件  
  
1.  在**“数据源”**窗口中展开**“Suppliers”**表。  
  
2.  单击**“Company Name”**节点上的下拉箭头并选择**“ComboBox”**。  
  
3.  将**“CompanyName”**从**“数据源”**窗口拖动到操作窗格控件中。  
  
     操作窗格控件中便会创建一个 <xref:System.Windows.Forms.ComboBox> 控件。  同时，会将一个名为 `SuppliersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、一个表适配器和一个 <xref:System.Data.DataSet> 添加到组件栏的项目中。  
  
4.  选择**“组件”**栏中的 `SuppliersBindingNavigator` 并按 Delete。  在此演练中您将不会使用 `SuppliersBindingNavigator`。  
  
    > [!NOTE]  
    >  删除 `SuppliersBindingNavigator` 并不会移除为其生成的所有代码。  您可以移除此代码。  
  
5.  移动组合框，使其位于标签之下，并将**“Size”**属性更改为“171, 21”。  
  
6.  在**“数据源”**窗口中，展开**“Suppliers”**表的子表**“Products”**。  
  
7.  单击**“ProductName”**节点上的下拉箭头，然后选择**“ListBox”**。  
  
8.  将**“ProductName”**拖动到操作窗格控件中。  
  
     操作窗格控件中便会创建一个 <xref:System.Windows.Forms.ListBox> 控件。  同时，会将一个名为 `ProductBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 和一个表适配器添加到组件栏的项目中。  
  
9. 移动列表框，使其位于标签之下，并将**“Size”**属性更改为“171,95”。  
  
10. 将 <xref:System.Windows.Forms.Button> 从**“工具箱”**拖动到操作窗格控件上，并将其置于列表框下面。  
  
11. 右击 <xref:System.Windows.Forms.Button>，单击快捷菜单上的**“属性”**并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**插入**|  
    |**文本**|**插入**|  
  
12. 调整用户控件的大小，使其适合这些控件。  
  
## 设置数据源  
 若要设置数据源，请将代码添加到操作窗格控件的 <xref:System.Windows.Forms.UserControl.Load> 事件以使用 <xref:System.Data.DataTable> 中的数据填充控件，并为每个控件设置 <xref:System.Windows.Forms.Binding.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 属性。  
  
#### 使用数据加载控件  
  
1.  在 `ActionsControl` 类的 <xref:System.Windows.Forms.UserControl.Load> 事件处理程序中，添加以下代码。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  在 C\# 中，必须将事件处理程序附加到 <xref:System.Windows.Forms.UserControl.Load> 事件。  可以将这些代码放在 `ActionsControl` 构造函数中 `InitializeComponent` 调用的后面。  有关如何创建事件处理程序的更多信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### 设置控件的数据绑定属性  
  
1.  选择 `CompanyNameComboBox` 控件。  
  
2.  在**“属性”**窗口中单击**“DataSource”**属性右侧的按钮，然后选择**“SuppliersBindingSource”**。  
  
3.  单击**“DisplayMember”**属性右侧的按钮，然后选择**“CompanyName”**。  
  
4.  展开**“DataBindings”**属性，单击**“Text”**属性右侧的按钮，然后选择**“None”**。  
  
5.  选择 `ProductNameListBox` 控件。  
  
6.  在**“属性”**窗口中单击**“DataSource”**属性右侧的按钮，然后选择**“productsBindingSource”**。  
  
7.  单击**“DisplayMember”**属性右侧的按钮，然后选择**“ProductName”**。  
  
8.  展开**“DataBindings”**属性，单击**“SelectedValue”**属性右侧的按钮，然后选择**“None”**。  
  
## 添加方法以将数据插入表中  
 下一个任务是从绑定控件中读取数据并填充 Word 文档中的表。  首先，创建一个用于设置表格标题格式的过程，然后添加 `AddData` 方法以创建一个 Word 表并设置其格式。  
  
#### 设置表格标题的格式  
  
1.  在 `ActionsControl` 类中创建一个方法，用以设置表格标题的格式。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### 创建表  
  
1.  在 `ActionsControl` 类中编写一个方法，此方法将在不存在表的情况下创建一个表，并将操作窗格中的数据添加到此表中。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### 在 Word 表中插入文本  
  
1.  将以下代码添加到**“插入”**按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  在 C\# 中，必须为按钮的 <xref:System.Windows.Forms.Control.Click> 事件创建事件处理程序。  可以将此代码放置在 `ActionsControl` 类的 <xref:System.Windows.Forms.UserControl.Load> 事件处理程序中。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## 显示操作窗格  
 将控件添加到操作窗格之后，操作窗格即变为可见。  
  
#### 显示操作窗格  
  
1.  在**“解决方案资源管理器”**中右击**“ThisDocument.vb”**或**“ThisDocument.cs”**，再单击快捷菜单上的**“查看代码”**。  
  
2.  在 `ThisDocument` 类的顶部创建一个新的控件实例，使其看上去与下面的示例类似。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  向 `ThisDocument` 的 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件处理程序中添加代码，使其看上去与下面的示例类似。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## 测试应用程序  
 现在可以对文档进行测试，以验证当文档打开时是否出现操作窗格。  测试操作窗格上控件之间的主\/从关系，并确保单击**“插入”**按钮时数据会填充到 Word 表中。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  确认操作窗格可见。  
  
3.  从组合框中选择一个公司，并确认**“Products”**列表框中的项随之发生变化。  
  
4.  选择一个产品，单击操作窗格上的**“插入”**，并确认产品详细信息会随之添加到 Word 表中。  
  
5.  插入来自不同公司的其他产品。  
  
## 后续步骤  
 此演练演示将数据绑定到 Word 操作窗格中的控件的基本操作。  以下是接下来可能要执行的一些任务：  
  
-   将数据绑定到 Excel 中的控件。  有关更多信息，请参见[演练：将数据绑定到 Excel 操作窗格上的控件](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)。  
  
-   部署项目。  有关更多信息，请参见[使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## 请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  