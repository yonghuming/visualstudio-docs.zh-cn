---
title: "演练： 针对 NamedRange 控件的事件进行编程 |Microsoft 文档"
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
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: "57"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40076f607e66ec76aaa42ae297d22b38a6234ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>演练：根据 NamedRange 控件的事件进行编程
  本演练演示如何添加<xref:Microsoft.Office.Tools.Excel.NamedRange>控件添加到 Microsoft Office Excel 工作表并针对通过使用 Visual Studio 中的 Office 开发工具使用其事件进行编程。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在本演练中，你将学会如何执行以下任务：  
  
-   添加<xref:Microsoft.Office.Tools.Excel.NamedRange>向工作表中的控件。  
  
-   对其进行编程<xref:Microsoft.Office.Tools.Excel.NamedRange>控制事件。  
  
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
  
1.  使用名称创建的 Excel 工作簿项目**我名为范围事件**。 请确保**创建新文档**选择。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Excel 工作簿并将添加**我名为范围事件**项目合并为**解决方案资源管理器**。  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>添加文本和名为向工作表范围  
 因为主机控件扩展 Office 对象，可以将它们添加到文档中的相同方式添加本机对象。 例如，你可以添加 Excel<xref:Microsoft.Office.Tools.Excel.NamedRange>到通过打开工作表的控件**插入**菜单上，指向**名称**，并选择**定义**。 你还可以添加<xref:Microsoft.Office.Tools.Excel.NamedRange>通过拖动从控件**工具箱**到工作表上。  
  
 在此步骤中，将两个命名的范围控件添加到工作表使用**工具箱**，然后将文本添加到工作表。  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>若要添加到工作表范围  
  
1.  验证**我名为范围 Events.xlsx**工作簿是在 Visual Studio 设计器中，打开与`Sheet1`显示。  
  
2.  从**Excel 控件**选项卡的工具箱拖<xref:Microsoft.Office.Tools.Excel.NamedRange>控件添加到单元格**A1**中`Sheet1`。  
  
     **添加 NamedRange 控件**对话框随即出现。  
  
3.  验证**$A$ 1**将显示在可编辑文本框中，并且该单元格**A1**选择。 如果不存在，请单击单元格**A1**以将其选中。  
  
4.  单击“确定”。  
  
     单元格**A1**将成为名为区域`namedRange1`。 在表中，没有可见指示但`namedRange1`出现在**名称**框 （位于左侧工作表的正上方） 单元格时**A1**选择。  
  
5.  添加另一个<xref:Microsoft.Office.Tools.Excel.NamedRange>控件添加到单元格**B3**。  
  
6.  验证**$B$ 3**将显示在可编辑文本框中，并且该单元格**B3**选择。 如果不存在，请单击单元格**B3**以将其选中。  
  
7.  单击“确定”。  
  
     单元格**B3**将成为名为区域`namedRange2`。  
  
#### <a name="to-add-text-to-your-worksheet"></a>将文本添加到你的工作表  
  
1.  在单元格中**A1**，键入以下文本：  
  
     **这是 NamedRange 控件的一个示例。**  
  
2.  在单元格中**A3** (左侧`namedRange2`)，键入以下文本：  
  
     **事件：**  
  
 在以下部分中，你将编写代码插入到文本`namedRange2`和修改属性的`namedRange2`控件以响应<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>， <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>，和<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>的事件`namedRange1`。  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>添加代码以响应 BeforeDoubleClick 事件  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>若要将文本插入到 NamedRange2 基于 BeforeDoubleClick 事件  
  
1.  在**解决方案资源管理器**，右键单击**Sheet1.vb**或**Sheet1.cs**和选择**查看代码**。  
  
2.  将代码添加因此`namedRange1_BeforeDoubleClick`事件处理程序如下所示：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  在 C# 中，你必须添加事件处理程序命名范围中所示<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>下面事件。 有关创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>添加代码以响应更改事件  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>若要将文本插入到 namedRange2 基于更改事件  
  
1.  将代码添加因此`NamedRange1_Change`事件处理程序如下所示：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  双击 Excel 范围中的单元格进入编辑模式，因为<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>事件发生时所选内容移动的范围之外，即使未文本发生更改。  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>添加代码以响应 SelectionChange 事件  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>若要将文本插入到 namedRange2 基于 SelectionChange 事件  
  
1.  将代码添加因此**NamedRange1_SelectionChange**事件处理程序如下所示：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  双击 Excel 范围中的单元格使所选内容将移动到范围，因为<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>事件之前发生<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>事件发生。  
  
## <a name="testing-the-application"></a>测试应用程序  
 现在你可以测试你的工作簿以验证该文本描述这些事件的<xref:Microsoft.Office.Tools.Excel.NamedRange>引发事件时，将控件插入到另一个命名范围。  
  
#### <a name="to-test-your-document"></a>测试文档  
  
1.  按 F5 运行项目。  
  
2.  将光标置于`namedRange1`，并确认文本有关<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>插入事件和注释插入到表。  
  
3.  双击内`namedRange1`，并确认文本有关<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>事件插入与中的红色斜体化文本`namedRange2`。  
  
4.  外部单击`namedRange1`并记下更改事件发生时退出编辑模式，即使没有对文本已进行更改。  
  
5.  更改中的文本`namedRange1`。  
  
6.  外部单击`namedRange1`，并确认文本有关<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>事件插入到的蓝色文本与`namedRange2`。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示对事件的编程的基础知识<xref:Microsoft.Office.Tools.Excel.NamedRange>控件。 以下是接下来可能要任务：  
  
-   部署项目。 有关详细信息，请参阅[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [如何： 调整 NamedRange 控件的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [如何： 向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  