---
title: "如何： 添加 Windows 窗体控件添加到 Office 文档 |Microsoft 文档"
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8044ede5e7a83028af305a906a1879807ade79a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>How to: Add Windows Forms Controls to Office Documents
  你可以在设计时在文档级项目中，将 Windows 窗体控件添加到 Microsoft Office Excel 和 Microsoft Office Word 文档。 在运行时，你可以在文档级自定义项和 VSTO 外接程序中添加控件。例如，你可以将 <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> 控件添加到工作表，以便用户可以从选项列表选择。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 本主题介绍了以下任务：  
  
-   [在设计时添加控件](#designtime)  
  
-   [在运行时在文档级项目中添加控件](#runtimedoclevel)  
  
-   [在运行时在 VSTO 外接程序中添加控件](#runtimeaddin)  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何执行 i： 将控件添加到文档图面在运行时？](http://go.microsoft.com/fwlink/?LinkId=132782)。  
  
##  <a name="designtime"></a>在设计时添加控件  
 有几种方式在设计时向文档级项目中的文档添加 Windows 窗体控件。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-drag-a-windows-forms-control-to-the-document"></a>若要将 Windows 窗体控件拖到文档  
  
1.  在 Visual Studio 中创建或打开 Excel 工作簿项目或 Word 文档项目，以使文档在设计器中可见。 有关创建项目的信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在**公共控件**选项卡**工具箱**，单击你想要添加，的控件，然后将其拖到文档。  
  
    > [!NOTE]  
    >  当在 Excel 中选择一个控件时， **“公式栏”** 中将显示 **=EMBED("WinForms.Control.Host","")**。 此文本是必需的并且不应删除。  
  
#### <a name="to-draw-a-windows-forms-control-on-the-document"></a>若要在文档中绘制 Windows 窗体控件  
  
1.  在 Visual Studio 中创建或打开 Excel 工作簿项目或 Word 文档项目，以使文档在设计器中可见。 有关创建项目的信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在**公共控件**选项卡**工具箱**，单击你想要添加的控件。  
  
3.  在文档中，单击希望要定位的控件的左上角位置，然后拖动到要定位的控件的右下角位置。  
  
     该控件将按指定的位置和大小添加到文档。  
  
    > [!NOTE]  
    >  当在 Excel 中选择一个控件时，你将看到**=EMBED("WinForms.Control.Host","")**中**公式栏**。 此文本是必需的并且不应删除。  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>若要通过右键单击控件将 Windows 窗体控件添加到文档  
  
1.  在 Visual Studio 中创建或打开 Excel 工作簿项目或 Word 文档项目，以使文档在设计器中可见。 有关创建项目的信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在**公共控件**选项卡**工具箱**，单击你想要添加的控件  
  
3.  在文档中，单击希望要添加的控件的位置。  
  
     该控件将以默认大小添加到文档。  
  
    > [!NOTE]  
    >  当在 Excel 中选择一个控件时， **“公式栏”** 中将显示 **=EMBED("WinForms.Control.Host","")**。 此文本是必需的并且不应删除。  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>若要通过双击控件将 Windows 窗体控件添加到文档  
  
1.  在 Visual Studio 中创建或打开 Excel 工作簿项目或 Word 文档项目，以使文档在设计器中可见。 有关创建项目的信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在**公共控件**选项卡**工具箱**，双击你想要添加的控件。  
  
     该控件将被添加到位于文档或活动窗格中心位置处的文档。  
  
    > [!NOTE]  
    >  当在 Excel 中选择一个控件时， **“公式栏”** 中将显示 **=EMBED("WinForms.Control.Host","")**。 此文本是必需的并且不应删除。  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>若要通过按下 ENTER 键将 Windows 窗体添加到文档  
  
1.  在 Visual Studio 中创建或打开 Excel 工作簿项目或 Word 文档项目，以使文档在设计器中可见。 有关创建项目的信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在**公共控件**选项卡**工具箱**，单击你想要添加，的控件，然后按 ENTER 键。  
  
     该控件将被添加到位于文档或活动窗格中心位置处的文档。  
  
    > [!NOTE]  
    >  当在 Excel 中选择一个控件时， **“公式栏”** 中将显示 **=EMBED("WinForms.Control.Host","")**。 此文本是必需的并且不应删除。  
  
##  <a name="runtimedoclevel"></a>在运行时在文档级项目中添加控件  
 你可以在运行时以编程方式向文档添加 Windows 窗体控件。 在 Word 中，请使用 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> 属性的方法。 在 Excel 中，使用的方法<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A>属性`Sheet`  *n* 类。 每种方法都具有好几个重载，使你能够以不同的方式指定控件的位置。  
  
 当在运行时向文档添加 Windows 窗体控件时，关闭文档时该控件将不会保存在文档中。 你可以在下次打开文档时重新创建该控件。 有关更多信息，请参见 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### <a name="to-add-a-windows-forms-control-at-run-time"></a>在运行时添加 Windows 窗体控件  
  
1.  使用一种方法具有名称添加\<*控件类*> (其中*控件类*是你想要添加，如 Windows 窗体控件的类名称<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>)。  
  
     下面的代码示例演示如何添加<xref:Microsoft.Office.Tools.Excel.Controls.Button>到单元格**C5**的`Sheet1`Excel 的文档级项目中。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a>在运行时在 VSTO 外接程序中添加控件  
 你可以在运行时以编程方式将 Windows 窗体控件添加到任何打开的文档。 首先，生成一个基于打开的文档或工作表的主机项。 然后，在 Word 中，使用新主机项的 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 属性的方法。 然后，在 Excel 中，使用新主机项的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 属性的方法。 每种方法都具有好几个重载，使你能够以不同的方式指定控件的位置。  
  
 当在运行时向文档添加 Windows 窗体控件时，关闭文档时该控件将不会保存在文档中。 你可以在下次打开文档时重新创建该控件。 有关更多信息，请参见 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 有关在 VSTO 外接程序项目中生成主机项的详细信息，请参阅[扩展 Word 文档和 Excel VSTO 外接程序在运行时中的工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
#### <a name="to-add-a-windows-forms-control-at-run-time"></a>在运行时添加 Windows 窗体控件  
  
1.  使用一种方法具有名称添加\<*控件类*> (其中*控件类*是你想要添加，如 Windows 窗体控件的类名称<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>)。  
  
    > [!NOTE]  
    >  在 VSTO 外接程序项目面向[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更高版本，必须添加对 Microsoft.Office.Tools.Excel.v4.0.Utilities.dll 或 Microsoft.Office.Tools.Word.v4.0.Utilities.dll 程序集的引用，然后才能访问添加\<*控件类*> 方法。  
  
     下面的代码示例演示了如何通过使用 Word VSTO 外接程序将 <xref:Microsoft.Office.Tools.Word.Controls.Button> 添加到活动文档的第一段。  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>另请参阅  
 [Windows 窗体上的控件 Office 文档概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何： 调整工作表单元格中的控件的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  