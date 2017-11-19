---
title: "演练： 更改工作表格式设置使用复选框控件 |Microsoft 文档"
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
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f10b0ed77dc9d5f97b6fc2fc4f218c86dafee41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>演练：使用 CheckBox 控件更改工作表格式设置
  本演练演示了使用 Microsoft Office Excel 工作表上的复选框来更改格式设置的基础知识。 将使用 Visual Studio 中的 Office 开发工具创建并将代码添加到你的项目。 若要查看结果为已完成的示例，请参阅 Excel 控件示例[Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在本演练中，你将学会如何执行以下任务：  
  
-   将文本和控件添加到工作表。  
  
-   设置文本格式时选择了某个选项。  
  
-   测试你的项目。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>创建项目  
 在此步骤中，你将使用 Visual Studio 创建的 Excel 工作簿项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Excel 工作簿项目**我 Excel 格式**。 请确保**创建新文档**选择。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Excel 工作簿并将添加**我 Excel 格式**项目合并为**解决方案资源管理器**。  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>将文本和控件添加到工作表  
 对于本演练中，您将需要三个<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>控件和一些以文本<xref:Microsoft.Office.Tools.Excel.NamedRange>控件。  
  
#### <a name="to-add-three-check-boxes"></a>若要添加三个复选框  
  
1.  验证工作簿是在 Visual Studio 设计器，并打开`Sheet1`处于打开状态。  
  
2.  从**公共控件**选项卡**工具箱**，拖动<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>控件或邻近的单元格的**B2**中**Sheet1**。  
  
3.  从**视图**菜单上，选择**属性**窗口。  
  
4.  请确保**Checkbox1**是可见的对象名称列表框中**属性**窗口中，并更改以下属性：  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**“文本”**|**加粗**|  
  
5.  将第二个复选框，或其附近单元格**B4**和更改以下属性：  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**“文本”**|**斜体**|  
  
6.  拖动一个第三个复选框，或其附近单元格**B6**和更改以下属性：  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**“文本”**|**下划线**|  
  
7.  在按住 CTRL 键的同时选择所有三个复选框控件。  
  
8.  在 Excel 中的格式选项卡的排列组中，单击**Align**，然后单击**左对齐**。  
  
     在左侧，并在你选择的第一个控件的位置对齐的三个复选框控件。  
  
     接下来，您将拖动<xref:Microsoft.Office.Tools.Excel.NamedRange>到工作表中的控件。  
  
    > [!NOTE]  
    >  你还可以添加<xref:Microsoft.Office.Tools.Excel.NamedRange>控件通过键入**textFont**到**名称**框。  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>将文本添加到 NamedRange 控件  
  
1.  从**Excel 控件**选项卡的工具箱拖<xref:Microsoft.Office.Tools.Excel.NamedRange>控件添加到单元格**B9**。  
  
2.  验证**$B$ 9**将显示在可编辑文本框中，并且该单元格**B9**选择。 如果不存在，请单击单元格**B9**以将其选中。  
  
3.  单击“确定”。  
  
4.  单元格**B9**将成为名为区域`NamedRange1`。  
  
     在表中，没有可见指示但`NamedRange1`出现在**名称框**（上方左侧工作表） 单元格时**B9**选择。  
  
5.  请确保**NamedRange1**是可见的对象名称列表框中**属性**窗口中，并更改以下属性：  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**textFont**|  
    |**Value2**|**单击复选框来更改此文本的格式设置。**|  
  
 接下来，编写代码以设置文本格式时选择了某个选项。  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>格式文本时选项被选中  
 在本部分中，你将编写代码，以便当用户选择的格式设置选项，更改了工作表中的文本的格式。  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>若要更改格式设置复选框时被选择  
  
1.  右键单击**Sheet1**，然后单击**查看代码**快捷菜单上。  
  
2.  以下代码添加到<xref:System.Windows.Forms.Control.Click>事件处理程序`applyBoldFont`复选框：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  以下代码添加到<xref:System.Windows.Forms.Control.Click>事件处理程序`applyItalicFont`复选框：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  以下代码添加到<xref:System.Windows.Forms.Control.Click>事件处理程序`applyUnderlineFont`复选框：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  在 C# 中，你必须添加到对应的复选框的事件处理程序<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件如下所示。 有关创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 你现在可以测试你的工作簿，以确保在选择或清除复选框文本的格式设置正确。  
  
#### <a name="to-test-your-workbook"></a>测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  选中或清除复选框。  
  
3.  确认文本格式正确。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示了使用复选框以及设置 Excel 工作表上的文本格式的基础知识。 以下是接下来可能要执行的一些任务：  
  
-   部署项目。 有关详细信息，请参阅[部署 Office 解决方案使用 clickonce](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
-   使用按钮填充文本框。 有关详细信息，请参阅[演练： 在工作表使用按钮的文本框中显示的文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [Office 文档上的 Windows 窗体控件限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  