---
title: "演练：使用 CheckBox 控件更改工作表格式设置"
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
  - "控件 [Visual Studio 中的 Office 开发], 添加到工作表"
  - "工作表, 使用托管控件更改格式"
  - "工作表, 复选框控件"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# 演练：使用 CheckBox 控件更改工作表格式设置
  此演练演示在 Microsoft Office Excel 工作表中使用复选框更改格式设置的基本操作。  您将使用 Visual Studio 中的 Office 开发工具创建代码并将代码添加到您的项目中。  若要查看结果（作为完整示例），请参见 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的 Excel 控件示例。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 通过本演练，您将学会如何执行以下任务：  
  
-   将文本和控件添加到工作表。  
  
-   选择选项时设置文本的格式。  
  
-   测试项目。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## 创建项目  
 在此步骤中，您将使用 Visual Studio 创建一个 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  创建一个名为“我的 Excel 格式设置”的 Excel 工作簿项目。  确保已选择**“创建新文档”**。  有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 在设计器中打开新的 Excel 工作簿，并将**“我的 Excel 格式设置”**项目添加到**“解决方案资源管理器”**中。  
  
## 将文本和控件添加到工作表  
 在此演练中，将需要三个 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 控件以及 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件中的一些文本。  
  
#### 添加三个复选框  
  
1.  验证工作簿是否已在 Visual Studio 设计器中打开且打开了 `Sheet1`。  
  
2.  从**“工具箱”**的**“公共控件”**选项卡上，将 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 控件拖动到**“Sheet1”**的单元格**“B2”**中或其附近。  
  
3.  从**“视图”**菜单中选择**“属性窗口”**。  
  
4.  确保**“Checkbox1”**在**“属性窗口”**的对象名称列表框中可见，然后更改以下属性：  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**applyBoldFont**|  
    |**文本**|Bold|  
  
5.  将第二个复选框拖动到单元格**“B4”**中或其附近，然后更改以下属性：  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**applyItalicFont**|  
    |**文本**|Italic|  
  
6.  将第三个复选框拖动到单元格**“B6”**中或其附近，然后更改以下属性：  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**applyUnderlineFont**|  
    |**文本**|Underline|  
  
7.  按住“Ctrl”键，将三个复选框控件全部选中。  
  
8.  在布局选项的位置组中在 Excel 中，单击 **对齐**，然后单击 **左对齐**。  
  
     三个复选框控件在左边对齐，在选择第一个控件的位置。  
  
     接下来，您要将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件拖动到工作表中。  
  
    > [!NOTE]  
    >  还可以通过在**“名称”**框中键入 **textFont** 添加 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
#### 将文本添加到 NamedRange 控件  
  
1.  从工具箱的**“Excel 控件”**选项卡中将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件拖动到单元格**“B9”**。  
  
2.  验证**“$B$9”**是否出现在可编辑的文本框中，并且单元格**“B9”**被选中。  如果不是这样，请单击单元格**“B9”**将其选中。  
  
3.  单击**“确定”**。  
  
4.  单元格**“B9”**变为名为 `NamedRange1` 的范围。  
  
     工作表上没有可见的指示，但是当单元格**“B9”**被选中时，`NamedRange1` 将出现在**“名称框”**（就在工作表左侧的上方）中。  
  
5.  确保**“NamedRange1”**在**“属性”**窗口的对象名称列表框中可见，然后更改以下属性：  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**textFont**|  
    |**Value2**|单击一个复选框以更改此文本的格式设置。|  
  
 然后，编写代码来在选中某一选项时设置文本的格式。  
  
## 选中选项时设置文本的格式  
 在本节中，您将编写代码，以使用户选择某个格式设置选项时工作表中文本的格式会发生变化。  
  
#### 选中复选框时更改格式设置  
  
1.  右击**“Sheet1”**，再单击快捷菜单上的**“查看代码”**。  
  
2.  将以下代码添加到 `applyBoldFont` 复选框的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  将以下代码添加到 `applyItalicFont` 复选框的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  将以下代码添加到 `applyUnderlineFont` 复选框的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  在 C\# 中，必须为复选框添加 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件的事件处理程序，如下所示。  有关创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## 测试应用程序  
 现在可以对工作簿进行测试，以确保在选择或清除一个复选框时正确设置文本的格式。  
  
#### 测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  选择或清除复选框。  
  
3.  确认文本的格式设置正确。  
  
## 后续步骤  
 此演练演示在 Excel 工作表中使用复选框和设置文本格式的基本操作。  下一步可能要执行以下几项任务：  
  
-   部署项目。  有关更多信息，请参见[使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
-   使用按钮填充文本框。  有关更多信息，请参见[演练：使用按钮在工作表的文本框中显示文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  
  
## 请参阅  
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [Office 文档上的 Windows 窗体控件的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  