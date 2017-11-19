---
title: "演练： 将数据绑定到 Word 操作窗格上的控件 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a70bd325a5a9e20f9a67e59f81c63ce4b1ddcc4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>演练：将数据绑定到“Word 操作”窗格上的控件
  本演练演示数据绑定到 Word 中的操作窗格上的控件。 控件演示 SQL Server 数据库中表之间的主/从关系。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   使用 Windows 窗体控件绑定到数据创建操作窗格。  
  
-   使用主/从关系显示控件中的数据。  
  
-   应用程序打开时，请显示操作窗格。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   到 Northwind SQL Server 示例数据库的服务器的访问。  
  
-   读取和写入到 SQL Server 数据库的权限。  
  
## <a name="creating-the-project"></a>创建项目  
 第一步是创建 Word 文档项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Word 文档项目**我的 Word 操作窗格**。 在向导中，选择**创建新文档**。  
  
     有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Word 文档和添加**我的 Word 操作窗格**项目合并为**解决方案资源管理器**。  
  
## <a name="adding-controls-to-the-actions-pane"></a>将控件添加到操作窗格  
 对于本演练中，你需要一个包含数据绑定 Windows 窗体控件的操作窗格控件。 将数据源添加到项目中，并将控件从**数据源**到操作窗格控件的窗口。  
  
#### <a name="to-add-an-actions-pane-control"></a>若要添加操作窗格控件  
  
1.  选择**我的 Word 操作窗格**项目中**解决方案资源管理器**。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
3.  在**添加新项**对话框中，选择**操作窗格控件**，将其命名为**ActionsControl**，然后单击**添加**。  
  
#### <a name="to-add-a-data-source-to-the-project"></a>若要将数据源添加到项目  
  
1.  如果 **“数据源”** 窗口不可见，则在菜单栏上，通过选择 **“查看”**， **“其他窗口”**、 **“数据源”**显示它。  
  
    > [!NOTE]  
    >  如果**显示数据源**不可用，单击 Word 文档，然后再次进行检查。  
  
2.  单击**添加新数据源**启动**数据源配置向导**。  
  
3.  选择**数据库**，然后单击**下一步**。  
  
4.  选择一个数据连接到 Northwind 示例 SQL Server 数据库，或通过添加新连接**新连接**按钮。  
  
5.  单击 **“下一步”**。  
  
6.  如果选中，将连接另存的选项，然后单击清除**下一步**。  
  
7.  展开**表**中的节点**数据库对象**窗口。  
  
8.  选中的复选框旁边**供应商**和**产品**表。  
  
9. 单击 **“完成”**。  
  
 该向导将添加**供应商**表和**产品**表**数据源**窗口。 它还将类型化数据集添加到项目中的可见**解决方案资源管理器**。  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>将数据绑定 Windows 窗体控件添加到操作窗格控件  
  
1.  在**数据源**窗口中，展开**供应商**表。  
  
2.  单击下拉箭头**公司名称**节点，然后选择**ComboBox**。  
  
3.  拖动**CompanyName**从**数据源**到操作窗格控件的窗口。  
  
     A<xref:System.Windows.Forms.ComboBox>在操作窗格控件创建控件。 同时，<xref:System.Windows.Forms.BindingSource>名为`SuppliersBindingSource`，一个表适配器和一个<xref:System.Data.DataSet>添加到组件栏中的项目。  
  
4.  选择`SuppliersBindingNavigator`中**组件**栏，然后按 DELETE。 你将不会使用`SuppliersBindingNavigator`在本演练中。  
  
    > [!NOTE]  
    >  删除`SuppliersBindingNavigator`不会删除所有已为其生成的代码。 你可以删除此代码。  
  
5.  移动组合框，以便它位于标签和更改**大小**属性**171，21**。  
  
6.  在**数据源**窗口中，展开**产品**，它是表的子**供应商**表。  
  
7.  单击下拉箭头**ProductName**节点，然后选择**ListBox**。  
  
8.  拖动**ProductName**到操作窗格控件。  
  
     A<xref:System.Windows.Forms.ListBox>在操作窗格控件创建控件。 同时，<xref:System.Windows.Forms.BindingSource>名为`ProductBindingSource`和表适配器添加到组件栏中的项目。  
  
9. 移动列表框中，以便它位于标签和更改**大小**属性**171，95**。  
  
10. 拖动<xref:System.Windows.Forms.Button>从**工具箱**拖到操作窗格控件并将它放置列表框下方。  
  
11. 右键单击<xref:System.Windows.Forms.Button>，单击**属性**的快捷菜单上，并更改以下属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**插入**|  
    |**“文本”**|**插入**|  
  
12. 调整用户控件以适合控件的大小。  
  
## <a name="setting-up-the-data-source"></a>设置数据源  
 若要设置数据源，将代码添加到<xref:System.Windows.Forms.UserControl.Load>操作窗格控件中的数据填充进度控件的事件<xref:System.Data.DataTable>，并设置<xref:System.Windows.Forms.Binding.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>为每个控件的属性。  
  
#### <a name="to-load-the-control-with-data"></a>若要加载的数据的控件  
  
1.  在<xref:System.Windows.Forms.UserControl.Load>事件处理程序`ActionsControl`类中，添加下面的代码。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  在 C# 中，你必须将附加到事件处理程序<xref:System.Windows.Forms.UserControl.Load>事件。 你可以将此代码放置在`ActionsControl`构造函数，在调用后的`InitializeComponent`。 有关如何创建事件处理程序的详细信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>若要设置数据绑定控件属性  
  
1.  选择 `CompanyNameComboBox` 控件。  
  
2.  在**属性**窗口中，单击右侧的按钮**数据源**属性，并选择**suppliersBindingSource**。  
  
3.  单击右侧的按钮**DisplayMember**属性，并选择**CompanyName**。  
  
4.  展开**DataBindings**属性，单击右侧的按钮**文本**属性，并选择**无**。  
  
5.  选择 `ProductNameListBox` 控件。  
  
6.  在**属性**窗口中，单击右侧的按钮**数据源**属性，并选择**productsBindingSource**。  
  
7.  单击右侧的按钮**DisplayMember**属性，并选择**ProductName**。  
  
8.  展开**DataBindings**属性，单击右侧的按钮**SelectedValue**属性，并选择**无**。  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>添加方法以向表中插入数据  
 下一个任务是从绑定控件中读取数据并填充 Word 文档中的表。 首先，创建一个用于设置在表中，标题格式的过程，然后添加`AddData`方法创建并设置 Word 表格的格式。  
  
#### <a name="to-format-the-table-headings"></a>若要设置格式的表标题  
  
1.  在`ActionsControl`类中，创建一个要设置格式的表标题中的方法。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>若要创建表  
  
1.  在`ActionsControl`类中，编写的方法，将创建一个表，如果有一个不已不存在，并将数据从操作窗格添加到表。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>若要向 Word 表中插入文本  
  
1.  以下代码添加到<xref:System.Windows.Forms.Control.Click>事件处理程序**插入**按钮。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  在 C# 中，你必须创建的事件处理程序<xref:System.Windows.Forms.Control.Click>该按钮的事件。  你可以将此代码放置在<xref:System.Windows.Forms.UserControl.Load>事件处理程序`ActionsControl`类。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>显示操作窗格  
 后向其添加控件时，操作窗格中将变得可见。  
  
#### <a name="to-show-the-actions-pane"></a>若要显示操作窗格  
  
1.  在**解决方案资源管理器**，右键单击**ThisDocument.vb**或**ThisDocument.cs**，然后单击**查看代码**快捷菜单上。  
  
2.  在顶部创建控件的新实例`ThisDocument`类，使其类似下面的示例所示。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  将代码添加到<xref:Microsoft.Office.Tools.Word.Document.Startup>事件处理程序`ThisDocument`以便其类似下面的示例所示。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 现在，你可以测试你的文档，以验证操作窗格中显示文档何时被打开。 测试在操作窗格上控件之间的主/从关系并确保数据 is populated in Word 表时**插入**单击按钮。  
  
#### <a name="to-test-your-document"></a>测试文档  
  
1.  按 F5 运行项目。  
  
2.  确认操作窗格可见。  
  
3.  组合框中选择一家公司，并验证中的项**产品**列表框中更改。  
  
4.  选择一个产品，请单击**插入**的操作窗格中，并验证所产品详细信息添加到 Word 表中。  
  
5.  从多个公司插入额外的产品。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示了将数据绑定到 Word 中操作窗格上的控件的基础知识。 以下是接下来可能要执行的一些任务：  
  
-   数据绑定到 Excel 中的控件。 有关详细信息，请参阅[演练： 将数据绑定到 Excel 操作窗格上的控件](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)。  
  
-   部署项目。 有关详细信息，请参阅[部署 Office 解决方案使用 clickonce](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## <a name="see-also"></a>另请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [如何： 向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  