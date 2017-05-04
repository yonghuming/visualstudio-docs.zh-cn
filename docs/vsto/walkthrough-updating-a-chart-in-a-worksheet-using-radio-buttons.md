---
title: "演练：使用单选按钮更新工作表中的图表 | Microsoft Docs"
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
  - "控件 [Visual Studio 中的 Office 开发], 更新工作表"
  - "工作表, 使用托管控件更新"
  - "工作表, 使用单选按钮"
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# 演练：使用单选按钮更新工作表中的图表
  此演练演示在 Microsoft Office Excel 工作表中使用单选按钮以供用户快速切换选项的基本操作。  在本例中，这些选项更改图表的样式。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 若要查看结果（作为完整示例），请参见 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的 Excel 控件示例。  
  
 本演练阐释了以下任务：  
  
-   将一组单选按钮添加到工作表。  
  
-   在选择某个选项时更改图表样式。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## 向工作表添加图表  
 可以创建一个 Excel 工作簿项目来自定义现有工作簿。  在此演练中，您将向工作簿中添加一个图表，然后再在新的 Excel 解决方案中使用此工作簿。  此演练中的数据源是一个名为**“Data for Chart”**的工作表。  
  
#### 添加数据  
  
1.  打开 Microsoft Excel。  
  
2.  右击**“Sheet3”**选项卡，然后单击快捷菜单上的**“重命名”**。  
  
3.  将该表重命名为“Data for Chart”。  
  
4.  将以下数据添加到**“Data for Chart”**中，其中单元格 A4 对应左上角的第一个数据，E8 对应于右下角的最后一个数据。  
  
    ||Q1|Q2|Q3|Q4|  
    |-|--------|--------|--------|--------|  
    |West|500|550|550|600|  
    |East|600|625|675|700|  
    |North|450|470|490|510|  
    |South|800|750|775|790|  
  
 接下来，向第一个工作表中添加一个图表以显示数据。  
  
#### 在 Excel 中添加图表  
  
1.  在**“插入”**选项卡上的**“图表”**组中，单击**“列”**，再单击**“所有图表类型”**。  
  
2.  在**“插入图表”**对话框中，单击**“确定”**。  
  
3.  在**“设计”**选项卡上的**“数据”**组中，单击**“选择数据”**。  
  
4.  在**“选择数据源”**对话框中，在**“图表数据范围”**框中单击，并清除任何默认选定内容。  
  
5.  在**“Data for Chart”**表中选择包含数字的单元格块，其中包括从左上角 A4 到右下角 E8 的单元格范围。  
  
6.  在**“选择数据源”**对话框中，单击**“确定”**。  
  
7.  重新放置图表，使单元格**“E2”**与右上角对齐。  
  
8.  将文件保存到驱动器 C 将其命名为 **ExcelChart.xlsx**。  
  
9. 退出 Excel。  
  
## 创建新项目  
 在此步骤中，您将创建一个基于**“ExcelChart”**工作簿的 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  创建一个名为**“My Excel Chart”**的 Excel 工作簿项目。  在向导中，选择**“复制现有文档”**。  
  
     有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  单击 **浏览** buttonand浏览到您在本演练中创建的工作簿。  
  
3.  单击**“确定”**。  
  
     Visual Studio 在设计器中打开新的 Excel 工作簿，并将**“My Excel Chart”**项目添加到**“解决方案资源管理器”**中。  
  
## 设置图表的属性  
 创建使用现有工作簿的新 Excel 工作簿项目时，会为工作簿中的所有现有命名范围、列表对象和图表自动创建宿主控件。  可以使用**“属性”**窗口更改 <xref:Microsoft.Office.Tools.Excel.Chart> 控件的名称。  
  
#### 更改 Chart 控件的名称  
  
1.  在设计器中选择 <xref:Microsoft.Office.Tools.Excel.Chart> 控件，并在**“属性”**窗口中更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## 添加控件  
 此工作表使用单选按钮让用户可以快速更改图表样式。  但是，单选按钮需要具有互斥性：一个按钮处于选中状态时，组中不能有其他按钮同时处于选中状态。  向工作表中添加多个单选按钮时不会默认具有此行为。  
  
 添加此行为的一种方法是将单选按钮分组到一个用户控件中，针对该用户控件编写代码，然后将该用户控件添加到工作表中。  
  
#### 添加用户控件  
  
1.  在**“解决方案资源管理器”**中选择**“My Excel Chart”**项目。  
  
2.  在**“项目”**菜单上，单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中单击**“用户控件”**，将控件命名为**“ChartOptions”**，然后单击**“添加”**。  
  
#### 向用户控件中添加单选按钮  
  
1.  如果该用户控件在设计器中不可见，请在**“解决方案资源管理器”**中双击**“ChartOptions”**。  
  
2.  从**“工具箱”**的**“公共控件”**选项卡中，将一个**“Radio Button”**控件拖动到该用户控件上，然后更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**columnChart**|  
    |**文本**|柱形图|  
  
3.  向该用户控件中添加第二个单选按钮，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**barChart**|  
    |**文本**|条形图|  
  
4.  向该用户控件中添加第三个单选按钮，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**lineChart**|  
    |**文本**|折线图|  
  
5.  向该用户控件中添加第四个单选按钮，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**areaBlockChart**|  
    |**文本**|面积图|  
  
 然后，编写代码，以在单击某一单选按钮时更新图表。  
  
## 在选中某一单选按钮时更改图表样式  
 现在，您可以添加代码以更改图表样式。  具体方法为：创建该用户控件的公共事件，添加属性设置选择类型，并为每个单选按钮的 `CheckedChanged` 事件创建事件处理程序。  
  
#### 创建用户控件的事件和属性  
  
1.  在**“解决方案资源管理器”**中右击用户控件，然后单击**“查看代码”**。  
  
2.  向 `ChartOptions` 类添加代码以创建 `SelectionChanged` 事件和 `Selection` 属性。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#13)]  
  
#### 处理单选按钮的 CheckedChanged 事件  
  
1.  设置 `areaBlockChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型，然后引发事件。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#14)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#14)]  
  
2.  设置 `barChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#15)]  
  
3.  设置 `columnChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#16)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#16)]  
  
4.  设置 `lineChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#17)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#17)]  
  
5.  在 C\# 中，必须为单选按钮添加事件处理程序。  可以将此代码添加到 `ChartOptions` 构造函数中的 `InitializeComponent` 调用的下面。  有关如何创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#18)]  
  
## 向工作表添加用户控件  
 生成解决方案时，新的用户控件将自动添加到**“工具箱”**中。  然后可以将该控件从**“工具箱”**拖动到工作表中。  
  
#### 向工作表添加用户控件  
  
1.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     **“ChartOptions”**用户控件便会被添加到**“工具箱”**中。  
  
2.  在**“解决方案资源管理器”**中，右击**“Sheet1.vb”**或**“Sheet1.cs”**，再单击**“视图设计器”**。  
  
3.  将**“ChartOptions”**控件从**“工具箱”**拖动到工作表中。  
  
     一个名为 `my_Excel_Chart_ChartOptions1` 的新控件便会被添加到项目中。  
  
4.  将该控件的名称更改为“ChartOptions1”。  
  
## 更改图表类型  
 若要更改图表类型，请创建一个事件处理程序，以根据在用户控件中选择的选项来设置样式。  
  
#### 更改工作表中显示的图表的类型  
  
1.  向 `Sheet1` 类添加以下事件处理程序。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#19)]  
  
2.  在 C\# 中，必须为用户控件向 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件添加事件处理程序，如下所示。  有关如何创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#20)]  
  
## 测试应用程序  
 现在便可对工作簿进行测试，验证选中某个单选按钮时是否可以正确设置图表样式。  
  
#### 测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  选择不同的单选按钮。  
  
3.  确认图表样式随所选选项发生了相应的更改。  
  
## 后续步骤  
 此演练演示在工作表中使用单选按钮和图表样式的基本操作。  下一步可能要执行以下几项任务：  
  
-   部署项目。  有关更多信息，请参见[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用按钮填充文本框。  有关更多信息，请参见[演练：使用按钮在工作表的文本框中显示文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  
  
-   使用复选框更改工作表的格式设置。  有关更多信息，请参见[演练：使用 CheckBox 控件更改工作表格式设置](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  
  
## 请参阅  
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)  
  
  