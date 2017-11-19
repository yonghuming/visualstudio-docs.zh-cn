---
title: "如何： 调整 ListObject 控件的大小 |Microsoft 文档"
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
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9aafcb9a131743c09d139f6f210c0d50425f4cba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-resize-listobject-controls"></a>如何：调整 ListObject 控件的大小
  将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到 Microsoft Office Excel 工作簿时，可以设置该控件的大小；但是，你可能需要在以后重设其大小。 例如，你可能希望将两列式列表更改为三列式列表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 在文档级项目中，可以在设计时或运行时重设 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的大小。 你可以在运行时在 VSTO 外接程序项目中重设 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的大小。  
  
 本主题介绍了以下任务：  
  
-   [在设计时重设 ListObject 控件的大小](#designtime)  
  
-   [在运行时在文档级项目中重设 ListObject 控件的大小](#runtimedoclevel)  
  
-   [在运行时在 VSTO 外接程序项目中重设 ListObject 控件的大小](#runtimeaddin)  
  
 有关 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的详细信息，请参阅 [ListObject Control](../vsto/listobject-control.md)。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何执行 i： 添加列与数据绑定列表对象在运行时？](http://go.microsoft.com/fwlink/?LinkID=130318)。  
  
##  <a name="designtime"></a> 在设计时重设 ListObject 控件的大小  
 若要重设列表的大小，可以单击并拖动其中一个尺寸控点，或者在“重设列表大小”  对话框中重新定义其大小。  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>使用“重设列表大小”对话框重设列表的大小  
  
  
1.  中单击任一处<xref:Microsoft.Office.Tools.Excel.ListObject>表。 **表工具、 设计**功能区中的选项卡将出现。  
  
2.  在属性部分中，单击**调整大小表**。  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  选择你的表的新数据范围。  
  
4.  单击“确定”。  
  
##  <a name="runtimedoclevel"></a> 在运行时在文档级项目中重设 ListObject 控件的大小  
 在运行时，可以使用 <xref:Microsoft.Office.Tools.Excel.ListObject> 方法重设 <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> 控件的大小。 不能使用此方法将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件移动到工作表中的新位置。 标题必须保持在同一行中，且重设大小后的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件必须与原列表对象重叠。 重设大小后的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件必须包含一个标题行，而且至少有一行数据。  
  
#### <a name="to-resize-a-list-object-programmatically"></a>以编程方式重设列表对象的大小  
  
1.  在 <xref:Microsoft.Office.Tools.Excel.ListObject> 上创建一个跨单元格“A1”  到“B3”  的 `Sheet1`控件。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  重设该列表的大小，使其包含单元格“A1”  到“C5” 。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> 在运行时在 VSTO 外接程序项目中重设 ListObject 的大小  
 你可以在运行时在任何打开的工作表中调整 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的大小。 有关如何使用 VSTO 外接程序向工作表添加 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的详细信息，请参阅 [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md)。  
  
#### <a name="to-resize-a-list-object-programmatically"></a>以编程方式重设列表对象的大小  
  
1.  在 <xref:Microsoft.Office.Tools.Excel.ListObject> 上创建一个跨单元格“A1”  到“B3”  的 `Sheet1`控件。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  重设该列表的大小，使其包含单元格“A1”  到“C5” 。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>另请参阅  
 [在运行时扩展 Word 文档和 Excel 工作簿在 VSTO 外接程序](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控件](../vsto/listobject-control.md)   
 [如何： 向工作表添加 ListObject 控件](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何： 调整书签控件的大小](../vsto/how-to-resize-bookmark-controls.md)   
 [如何：调整 NamedRange 控件的大小](../vsto/how-to-resize-namedrange-controls.md)  
  
  