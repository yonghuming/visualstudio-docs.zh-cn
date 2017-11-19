---
title: "演练： 将数据绑定到 Excel 操作窗格上的控件 |Microsoft 文档"
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
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e47f9083629ac66e0e195feb089a589c69a22789
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-binding-data-to-controls-on-an-excel-actions-pane"></a>演练：将数据绑定到 Excel 操作窗格上的控件
  本演练演示对 Microsoft Office Excel 中的操作窗格上的控件的数据绑定。 控件演示 SQL Server 数据库中表之间的主/从关系。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   将控件添加到工作表。  
  
-   创建操作窗格控件。  
  
-   将数据绑定 Windows 窗体控件添加到操作窗格控件。  
  
-   当应用程序打开时，请显示操作窗格。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   到 Northwind SQL Server 示例数据库的服务器的访问。  
  
-   读取和写入到 SQL Server 数据库的权限。  
  
## <a name="creating-the-project"></a>创建项目  
 第一步是创建一个 Excel 工作簿项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Excel 工作簿项目**我 Excel 操作窗格**。 在向导中，选择**创建新文档**。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Excel 工作簿并将添加**我 Excel 操作窗格**项目合并为**解决方案资源管理器**。  
  
## <a name="adding-a-new-data-source-to-the-project"></a>向项目添加新的数据源  
  
#### <a name="to-add-a-new-data-source-to-the-project"></a>若要向项目添加新的数据源  
  
1.  如果 **“数据源”** 窗口不可见，则在菜单栏上，通过选择 **“查看”**， **“其他窗口”**、 **“数据源”**显示它。  
  
2.  选择 **“添加新数据源”** 以启动 **“数据源配置向导”**。  
  
3.  选择**数据库**，然后单击**下一步**。  
  
4.  选择一个数据连接到 Northwind 示例 SQL Server 数据库，或通过添加新连接**新连接**按钮。  
  
5.  单击 **“下一步”**。  
  
6.  如果选中，将连接另存的选项，然后单击清除**下一步**。  
  
7.  展开**表**中的节点**数据库对象**窗口。  
  
8.  选中的复选框旁边**供应商**表。  
  
9. 展开**产品**表，然后选择**ProductName**，**供应商 Id**， **QuantityPerUnit**，和**UnitPrice**.  
  
10. 单击 **“完成”**。  
  
 该向导将添加**供应商**表和**产品**表**数据源**窗口。 它还将类型化数据集添加到项目中的可见**解决方案资源管理器**。  
  
## <a name="adding-controls-to-the-worksheet"></a>向工作表添加控件  
 接下来，添加<xref:Microsoft.Office.Tools.Excel.NamedRange>控件和<xref:Microsoft.Office.Tools.Excel.ListObject>控件添加到第一个工作表。  
  
#### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>若要添加 NamedRange 控件和 ListObject 控件  
  
1.  验证**我 Excel 操作 Pane.xlsx**工作簿是在 Visual Studio 设计器中，打开与`Sheet1`显示。  
  
2.  在**数据源**窗口中，展开**供应商**表。  
  
3.  单击下拉箭头**公司名称**节点，，然后单击**NamedRange**。  
  
4.  拖动**公司名称**从**数据源**到单元格的窗口**A2**中`Sheet1`。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>控件名为`CompanyNameNamedRange`创建和文本\<CompanyName > 出现在单元格中**A2**。 同时，<xref:System.Windows.Forms.BindingSource>名为`suppliersBindingSource`，一个表适配器和一个<xref:System.Data.DataSet>添加到项目。 该控件绑定到<xref:System.Windows.Forms.BindingSource>，后者又绑定到<xref:System.Data.DataSet>实例。  
  
5.  在**数据源**窗口中，之后的列下的向下滚动**供应商**表。 列表的底部是**产品**表; 这是此处，因为它是的子级**供应商**表。 选择此**产品**表，不是在与相同的级别才**供应商**表，，然后单击显示的下拉箭头。  
  
6.  单击**ListObject**在下拉列表中，然后拖动**产品**表添加到单元格**A6**中`Sheet1`。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>控件名为`ProductNameListObject`单元格中创建**A6**。 同时，<xref:System.Windows.Forms.BindingSource>名为`productsBindingSource`和表适配器添加到项目。 该控件绑定到<xref:System.Windows.Forms.BindingSource>，后者又绑定到<xref:System.Data.DataSet>实例。  
  
7.  仅适用于 C#，选择**suppliersBindingSource**上的组件栏和更改**修饰符**属性**内部**中**属性**窗口。  
  
## <a name="adding-controls-to-the-actions-pane"></a>将控件添加到操作窗格  
 接下来，你需要一个包含一个组合框的操作窗格控件。  
  
#### <a name="to-add-an-actions-pane-control"></a>若要添加操作窗格控件  
  
1.  选择**我 Excel 操作窗格**项目中**解决方案资源管理器**。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
3.  在**添加新项**对话框中，选择**操作窗格控件**，将其命名为**ActionsControl**，然后单击**添加**。  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>将数据绑定 Windows 窗体控件添加到操作窗格控件  
  
1.  从**公共控件**选项卡**工具箱**，拖动<xref:System.Windows.Forms.ComboBox>到操作窗格控件的控件。  
  
2.  更改**大小**属性**171，21**。  
  
3.  调整用户控件以适合组合框的大小。  
  
## <a name="binding-the-control-on-the-actions-pane-to-data"></a>操作窗格上的控件绑定到数据  
 在本部分中，您将设置的数据源的<xref:System.Windows.Forms.ComboBox>到同一数据源作为<xref:Microsoft.Office.Tools.Excel.NamedRange>工作表上的控件。  
  
#### <a name="to-set-data-binding-properties-of-the-control"></a>若要设置控件的数据绑定属性  
  
1.  右键单击操作窗格控件，并依次**查看代码**。  
  
2.  以下代码添加到<xref:System.Windows.Forms.UserControl.Load>操作窗格控件的事件。  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  在 C# 中，你必须创建的事件处理程序`ActionsControl`。 你可以将此代码放置在`ActionsControl`构造函数。 有关创建事件处理程序的详细信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="showing-the-actions-pane"></a>显示操作窗格  
 操作窗格不可见，直到你在运行时添加控件。  
  
#### <a name="to-show-the-actions-pane"></a>若要显示操作窗格  
  
1.  在**解决方案资源管理器**，右键单击 ThisWorkbook.vb 或 ThisWorkbook.cs，，然后单击**查看代码**。  
  
2.  创建用户控件中的新实例`ThisWorkbook`类。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  在<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>事件处理程序`ThisWorkbook`，将控件添加到操作窗格。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 现在，你可以测试您的文档以验证操作窗格打开时打开该文档，并且控件具有主/从关系。  
  
#### <a name="to-test-your-document"></a>测试文档  
  
1.  按 F5 运行项目。  
  
2.  确认操作窗格可见。  
  
3.  在列表框中选择一家公司。 验证公司名称列在<xref:Microsoft.Office.Tools.Excel.NamedRange>控制和中列出的产品详细信息<xref:Microsoft.Office.Tools.Excel.ListObject>控件。  
  
4.  选择不同的公司，以验证的公司名称和适当产品详细信息的更改。  
  
## <a name="next-steps"></a>后续步骤  
 以下是接下来可能要执行的一些任务：  
  
-   数据绑定到 Word 中的控件。 有关详细信息，请参阅[演练： 将数据绑定到 Word 操作窗格上的控件](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
-   部署项目。 有关详细信息，请参阅[部署 Office 解决方案使用 clickonce](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## <a name="see-also"></a>另请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [如何： 管理操作窗格上的控件布局](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  