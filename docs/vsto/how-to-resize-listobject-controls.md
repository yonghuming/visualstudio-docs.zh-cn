---
title: "如何：调整 ListObject 控件的大小"
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
  - "控件 [Visual Studio 中的 Office 开发]，重设大小"
  - "ListObject 控件，重设大小"
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：调整 ListObject 控件的大小
  将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件添加到 Microsoft Office Excel 工作簿时，可以设置该控件的大小；但是，你可能需要在以后重设其大小。 例如，你可能希望将两列式列表更改为三列式列表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 在文档级项目中，可以在设计时或运行时重设 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的大小。 你可以在运行时在 VSTO 外接程序项目中重设 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的大小。  
  
 本主题介绍了以下任务：  
  
-   [在设计时重设 ListObject 控件的大小](#designtime)  
  
-   [在运行时在文档级项目中重设 ListObject 控件的大小](#runtimedoclevel)  
  
-   [在运行时在 VSTO 外接程序项目中重设 ListObject 控件的大小](#runtimeaddin)  
  
 有关 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的详细信息，请参阅 [ListObject 控件](../vsto/listobject-control.md)。  
  
 ![链接到视频](../vsto/media/playvideo.png "链接到视频") 相关视频演示，请参阅[如何实现：在运行时向数据绑定列表对象添加列？）](http://go.microsoft.com/fwlink/?LinkID=130318)。  
  
##  <a name="designtime"></a> 在设计时重设 ListObject 控件的大小  
 若要重设列表的大小，可以单击并拖动其中一个尺寸控点，或者在“重设列表大小”对话框中重新定义其大小。  
  
#### 使用“重设列表大小”对话框重设列表的大小  
  
1.  右击 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  
  
2.  指向“列表”，然后在快捷菜单中单击“重设列表大小”。  
  
3.  选择要用来定义列表大小的单元格。  
  
4.  单击“确定”。  
  
##  <a name="runtimedoclevel"></a> 在运行时在文档级项目中重设 ListObject 控件的大小  
 在运行时，可以使用 <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> 方法重设 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的大小。 不能使用此方法将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件移动到工作表中的新位置。 标题必须保持在同一行中，且重设大小后的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件必须与原列表对象重叠。 重设大小后的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件必须包含一个标题行，而且至少有一行数据。  
  
#### 以编程方式重设列表对象的大小  
  
1.  在 `Sheet1` 上创建一个跨单元格“A1”到“B3”的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#6)]  
  
2.  重设该列表的大小，使其包含单元格“A1”到“C5”。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> 在运行时在 VSTO 外接程序项目中重设 ListObject 的大小  
 你可以在运行时在任何打开的工作表中调整 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的大小。 有关如何使用 VSTO 外接程序向工作表添加 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件的详细信息，请参阅 [如何：向工作表添加 ListObject 控件](../vsto/how-to-add-listobject-controls-to-worksheets.md)。  
  
#### 以编程方式重设列表对象的大小  
  
1.  在 `Sheet1` 上创建一个跨单元格“A1”到“B3”的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#12)]  
  
2.  重设该列表的大小，使其包含单元格“A1”到“C5”。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#13)]  
  
## 请参阅  
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控件](../vsto/listobject-control.md)   
 [如何：向工作表添加 ListObject 控件](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何：调整 Bookmark 控件的大小](../vsto/how-to-resize-bookmark-controls.md)   
 [如何：调整 NamedRange 控件的大小](../vsto/how-to-resize-namedrange-controls.md)  
  
  