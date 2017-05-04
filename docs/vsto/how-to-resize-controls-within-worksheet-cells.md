---
title: "如何：调整工作表单元格中的控件的大小 | Microsoft Docs"
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
  - "控件 [Visual Studio 中的 Office 开发], 调整大小"
  - "托管控件, 调整大小"
  - "Windows 窗体控件 [Visual Studio 中的 Office 开发], 调整大小"
  - "工作表, 调整大小"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 如何：调整工作表单元格中的控件的大小
  调整工作表的列和行的大小时，单元格中所包含的任何宿主控件都将自动调整到该单元格调整后的高度或宽度。  默认情况下，Windows 窗体控件不会自动调整大小。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 如果在设计时添加了这些控件，则必须为每个控件设置定位选项。  
  
 如果以编程方式添加 Windows 窗体控件并提供了范围参数，则当调整范围内的单元格的大小时，也将自动调整该控件的大小。  有关更多信息，请参见[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## 在设计时调整控件大小  
  
#### 使控件在设计时随单元格调整大小  
  
1.  将一个 Windows 窗体控件从**“工具箱”**拖动到工作表。  
  
2.  右击该控件，然后单击**“设置控件格式”**。  
  
3.  在**“设置控件格式”**对话框中，单击**“属性”**选项卡。  
  
4.  在**“对象位置”**下选择**“大小、位置随单元格而变”**选项，然后单击**“确定”**。  
  
     当调整包含该控件的单元格的大小时，也将调整该控件的大小，以使其适合单元格的大小。  
  
## 在运行时调整控件大小  
 如果在运行时添加一个 Windows 窗体控件并将 <xref:Microsoft.Office.Interop.Excel.Range> 作为该控件位置传入，则当调整包含该范围的工作表单元格的大小时，该控件将自动调整自身的大小。  
  
#### 使控件在运行时随单元格调整大小  
  
1.  将一个控件添加到 A1 范围。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     当调整包含该控件的单元格的大小时，也将调整该控件的大小，以使其适合单元格的大小。  
  
## 重置控件位置  
 通过将 `Placement` 属性设置为以下 <xref:Microsoft.Office.Interop.Excel.XlPlacement> 值之一，可以重置控件的位置并调整它的大小：  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### 更改控件的行为使其位置和大小不随单元格而变  
  
1.  调用控件的 placement 属性并将该值设置为 <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## 请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [如何：为 Office 文档添加 Windows 窗体控件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：在打印时隐藏工作表的控件](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office 文档上的 Windows 窗体控件的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  