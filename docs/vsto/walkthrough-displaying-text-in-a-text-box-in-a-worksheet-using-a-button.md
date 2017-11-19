---
title: "演练： 使用按钮在工作表的文本框中显示文本 |Microsoft 文档"
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
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b95eb6eeb5f8615f8f471ad33139afa49d5633f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>演练：使用按钮在工作表的文本框中显示文本
  本演练演示在 Microsoft Office Excel 工作表，以及如何创建使用 Visual Studio 中的 Office 开发工具的 Excel 项目中使用按钮和文本框的基础知识。 若要查看结果为已完成的示例，请参阅 Excel 控件示例[Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在本演练中，你将学会如何执行以下任务：  
  
-   将控件添加到工作表。  
  
-   单击按钮时，将填充文本框。  
  
-   测试你的项目。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>创建项目  
 在此步骤中，将创建使用 Visual Studio 的 Excel 工作簿项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Excel 工作簿项目**我的 Excel 按钮**。 请确保**创建新文档**选择。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Excel 工作簿并将添加**我的 Excel 按钮**项目合并为**解决方案资源管理器**。  
  
## <a name="adding-controls-to-the-worksheet"></a>向工作表添加控件  
 对于本演练中，你将需要一个按钮和第一个工作表上的文本框。  
  
#### <a name="to-add-a-button-and-a-text-box"></a>添加一个按钮和一个文本框  
  
1.  验证**我 Excel Button.xlsx**工作簿是在 Visual Studio 设计器中，打开与`Sheet1`显示。  
  
2.  从**公共控件**选项卡的工具箱拖<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>到`Sheet1`。  
  
3.  从**视图**菜单上，选择**属性窗口**。  
  
4.  请确保**TextBox1**中可以看见**属性**窗口下拉框，然后**名称**向文本框的属性**displayText**.  
  
5.  拖动**按钮**控件拖动到`Sheet1`和更改以下属性：  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**“文本”**|**插入文本**|  
  
 现在编写代码以在单击按钮时运行。  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>单击该按钮时将填充文本框中  
 用户单击此按钮时，每次**Hello World ！** 将追加到文本框中。  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>在单击按钮时写入文本框  
  
1.  在**解决方案资源管理器**，右键单击**Sheet1**，然后单击**查看代码**快捷菜单上。  
  
2.  以下代码添加到<xref:System.Windows.Forms.Control.Click>按钮事件处理程序：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  在 C# 中，你必须添加到事件处理程序<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件如下所示。 有关创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 你现在可以测试你的工作簿，若要确保消息**Hello World ！** 当单击按钮时，在文本框中出现。  
  
#### <a name="to-test-your-workbook"></a>测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  单击按钮。  
  
3.  确认**Hello World ！** 显示在文本框中。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示使用 Excel 工作表上的按钮和文本框的基础知识。 以下是接下来可能要执行的一些任务：  
  
-   部署项目。 有关详细信息，请参阅[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用复选框来更改格式设置。 有关详细信息，请参阅[演练： 更改工作表格式使用复选框控件](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 添加 Windows 窗体控件添加到 Office 文档](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)   
 [Office 文档上的 Windows 窗体控件限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  