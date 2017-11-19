---
title: "演练： 更新使用单选按钮在工作表的图表 |Microsoft 文档"
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
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74bd005514fa2fe72450a95d84f38dd17a7b639f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>演练：使用单选按钮更新工作表中的图表
  本演练演示了使用 Microsoft Office Excel 工作表上的单选按钮，使用户可以快速选项之间切换方式的基础知识。 在这种情况下，选项更改图表样式。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 若要查看结果为已完成的示例，请参阅 Excel 控件示例[Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)。  
  
 本演练阐释了以下任务：  
  
-   将一组单选按钮添加到工作表。  
  
-   在选择了某个选项时更改图表样式。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="adding-a-chart-to-a-worksheet"></a>向工作表添加图表  
 你可以创建自定义现有工作簿的 Excel 工作簿项目。 在此演练中，你将向工作簿添加图表，然后使用新的 Excel 解决方案中的此工作簿。 本演练中的数据源是名为一个工作表**图表数据**。  
  
#### <a name="to-add-the-data"></a>将数据添加  
  
1.  打开 Microsoft Excel。  
  
2.  右键单击**Sheet3**选项卡上，并依次**重命名**快捷菜单上。  
  
3.  重命名为表**图表数据**。  
  
4.  添加到以下数据**图表数据**与 A4 的单元格的左上角和 E8 右下角。  
  
    ||Q1|季 2 季|第 3 季度|第 4 季度|  
    |-|--------|--------|--------|--------|  
    |西部|500|550|550|600|  
    |东部|600|625|675|400|  
    |北美|450|470|490|510|  
    |南部|800|750|775|790|  
  
 接下来，将图表添加到第一个工作表中，以显示数据。  
  
#### <a name="to-add-a-chart-in-excel"></a>若要在 Excel 中添加图表  
  
1.  上**插入**选项卡上，在**图表**组中，单击**列**，然后单击**所有图表类型**。  
  
2.  在**插入图表**对话框中，单击**确定**。  
  
3.  上**设计**选项卡上，在**数据**组中，单击**选择数据**。  
  
4.  在**选择数据源**对话框中，单击**Chartdata 范围**框，并清除所有默认选择。  
  
5.  在**图表数据**表中，选择包含的数值，将其包括 A4 在左上角到 E8 右下角中的单元格的块。  
  
6.  在**选择数据源**对话框中，单击**确定**。  
  
7.  重新定位图表，以便与单元格的右上角对齐**E2**。  
  
8.  将文件保存到 C 驱动器并将其命名**ExcelChart.xlsx**。  
  
9. 退出 Excel。  
  
## <a name="creating-a-new-project"></a>创建新项目  
 在此步骤中，你将创建基于的 Excel 工作簿项目**ExcelChart**工作簿。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Excel 工作簿项目**我 Excel 图表**。 在向导中，选择**复制现有文档**。  
  
     有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  单击**浏览**buttonand 浏览到你在本演练前面创建的工作簿。  
  
3.  单击“确定”。  
  
     Visual Studio 将在设计器中打开新的 Excel 工作簿并将添加**我 Excel 图表**项目合并为**解决方案资源管理器**。  
  
## <a name="setting-properties-of-the-chart"></a>设置图表的属性  
 当你创建新的 Excel 工作簿项目使用的现有工作簿时，主机控件将自动创建为所有已命名的范围、 列表对象和工作簿中的图表。 你可以更改名称<xref:Microsoft.Office.Tools.Excel.Chart>控件通过使用**属性**窗口。  
  
#### <a name="to-change-the-name-of-the-chart-control"></a>若要更改图表控件的名称  
  
1.  选择<xref:Microsoft.Office.Tools.Excel.Chart>设计器中控制和更改中的以下属性**属性**窗口。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="adding-controls"></a>添加控件  
 此工作表使用单选按钮，用户可以快速地将更改图表样式。 但是，需要是排它性单选按钮-在同一时间时选择一个按钮时，可以选择在组中的没有其他按钮。 此行为不会默认发生时向工作表添加多个单选按钮。  
  
 添加此行为是上一个用户控件，将单选按钮分组的一种方法编写你的代码隐藏用户控件，然后将用户控件添加到工作表。  
  
#### <a name="to-add-a-user-control"></a>要添加用户控件  
  
1.  选择**我 Excel 图表**项目中**解决方案资源管理器**。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
3.  在**添加新项**对话框中，单击**用户控件**，命名该控件**ChartOptions，**单击**添加**。  
  
#### <a name="to-add-radio-buttons-to-the-user-control"></a>若要添加到用户控件的单选按钮  
  
1.  如果用户控件不可见设计器中，双击**ChartOptions**中**解决方案资源管理器**。  
  
2.  从**公共控件**选项卡**工具箱**，拖动**单选按钮**控制到用户控件，并可以更改以下属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**columnChart**|  
    |**“文本”**|**柱形图**|  
  
3.  将第二个单选按钮添加到用户控件，并更改以下属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**“文本”**|**条形图**|  
  
4.  将第三个单选按钮添加到用户控件，并更改以下属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**“文本”**|**折线图**|  
  
5.  将第四个单选按钮添加到用户控件，并更改以下属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**areaBlockChart**|  
    |**“文本”**|**面积图**|  
  
 接下来，编写的代码来更新该图表，单击一个单选按钮时。  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>选择更改图表样式时某一单选按钮  
 现在你可以添加代码以更改图表样式。 若要执行此操作，创建的公共事件的用户控件、 将属性设置所选内容类型中，添加和创建的事件处理程序`CheckedChanged`的每个单选按钮的事件。  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>创建用户控件的事件和属性  
  
1.  在**解决方案资源管理器**，右击用户控件，，然后单击**查看代码**。  
  
2.  将代码添加到`ChartOptions`类，以创建`SelectionChanged`事件和`Selection`属性。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
#### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>若要处理的 CheckedChanged 事件的单选按钮  
  
1.  设置 `CheckedChanged` 单选按钮的 `areaBlockChart` 事件处理程序中的图表类型，然后引发事件。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  
  
2.  设置 `CheckedChanged` 单选按钮的 `barChart` 事件处理程序中的图表类型。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  
  
3.  设置 `CheckedChanged` 单选按钮的 `columnChart` 事件处理程序中的图表类型。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  
  
4.  设置 `CheckedChanged` 单选按钮的 `lineChart` 事件处理程序中的图表类型。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  
  
5.  在 C# 中，必须为单选按钮添加事件处理程序。 可以将此代码添加到 `ChartOptions` 构造函数中 `InitializeComponent` 调用的下面。 有关如何创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="adding-the-user-control-to-the-worksheet"></a>将用户控件添加到工作表  
 生成解决方案时，新的用户控件自动添加到**工具箱**。 然后，可以将控件从**工具箱**到工作表。  
  
#### <a name="to-add-the-user-control-your-worksheet"></a>将用户控件添加你的工作表  
  
1.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     **ChartOptions**用户控件添加到**工具箱**。  
  
2.  在**解决方案资源管理器**，右键单击**Sheet1.vb**或**Sheet1.cs**，然后单击**视图设计器**。  
  
3.  拖动**ChartOptions**控件从**工具箱**到工作表。  
  
     一个名为的新控件`my_Excel_Chart_ChartOptions1`添加到你的项目。  
  
4.  更改该控件的名称**ChartOptions1**。  
  
## <a name="changing-the-chart-type"></a>更改图表类型  
 若要更改图表类型，创建的事件处理程序设置根据用户控件中选择的选项的样式。  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>若要更改的工作表中显示的图表类型  
  
1.  向 `Sheet1` 类添加以下事件处理程序。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  在 C# 中，你必须添加的事件处理程序的用户控件<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件如下所示。 有关如何创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 你现在可以测试你的工作簿以验证图表样式正确选择单选按钮时。  
  
#### <a name="to-test-your-workbook"></a>测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  选择不同的单选按钮。  
  
3.  确认图表样式随所选选项发生了相应的更改。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示使用工作表上的单选按钮和图表样式的基础知识。 以下是接下来可能要执行的一些任务：  
  
-   部署项目。 有关详细信息，请参阅[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用按钮填充文本框。 有关详细信息，请参阅[演练： 在工作表使用按钮的文本框中显示的文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  
  
-   更改格式设置的工作表上，通过使用复选框。 有关详细信息，请参阅[演练： 更改工作表格式使用复选框控件](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)  
  
  