---
title: "如何：调整 NamedRange 控件的大小 | Microsoft Docs"
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
  - "NamedRange 控件，调整大小"
  - "范围，在 Excel 中调整大小"
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 如何：调整 NamedRange 控件的大小
  将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件添加到 Microsoft Office Excel 文档时，可以设置该控件的大小；但是，你可能需要在以后调整其大小。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 在文档级项目中，可以在设计时或运行时调整命名范围的大小。 还可以在运行时在应用程序级 VSTO 外接程序中调整命名范围的大小。  
  
 本主题介绍了以下任务：  
  
-   [在设计时调整 NamedRange 控件的大小](#designtime)  
  
-   [在运行时，在文档级项目中调整 NamedRange 控件的大小](#runtimedoclevel)  
  
-   [在运行时，在 VSTO 外接程序项目中调整 NamedRange 控件的大小](#runtimeaddin)  
  
##  <a name="designtime"></a> 在设计时调整 NamedRange 控件的大小  
 可以通过在“定义名称”对话框中重新定义其大小来调整命名范围的大小。  
  
#### 使用“定义名称”对话框来调整命名范围的大小  
  
1.  右击 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
2.  在快捷菜单上单击“管理命名范围”。  
  
     “定义名称”对话框随即出现。  
  
3.  选择要调整大小的命名范围。  
  
4.  清除**引用**框。  
  
5.  选择要用来定义命名范围大小的单元格。  
  
6.  单击“确定”。  
  
##  <a name="runtimedoclevel"></a> 在运行时，在文档级项目中调整 NamedRange 控件的大小  
 可以通过编程的方式，使用 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> 属性调整命名范围的大小。  
  
> [!NOTE]  
>  在“属性”窗口中，<xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> 属性标记为“只读”。  
  
#### 以编程方式调整命名范围大小  
  
1.  在 `Sheet1` 的单元格 **A1** 中创建一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#4)]  
  
2.  调整命名范围的大小，使其包含单元格 **B1**。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> 在运行时，在 VSTO 外接程序项目中调整 NamedRange 控件的大小  
 你可以在运行时在任何打开的工作表中调整 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的大小。 有关如何使用 VSTO 外接程序向工作表添加 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的详细信息，请参阅 [如何：向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)。  
  
#### 以编程方式调整命名范围大小  
  
1.  在 `Sheet1` 的单元格 **A1** 中创建一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#10)]  
  
2.  调整命名范围的大小，使其包含单元格 **B1**。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#11)]  
  
## 请参阅  
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [如何：向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [如何：调整 Bookmark 控件的大小](../vsto/how-to-resize-bookmark-controls.md)   
 [如何：调整 ListObject 控件的大小](../vsto/how-to-resize-listobject-controls.md)  
  
  