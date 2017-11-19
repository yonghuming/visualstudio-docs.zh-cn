---
title: "如何： 调整工作表单元格中的控件的大小 |Microsoft 文档"
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
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 035021b3a49bd3fb2af2863e3c8a9b2f88c56077
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>如何：调整工作表单元格中的控件的大小
  当您调整列或行的工作表上时，自动包含的单元中的所有主机控件都调整为的高度或调整了大小的单元格的宽度。 默认情况下，Windows 窗体控件不自动调整。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 如果在设计时添加控件，则必须设置定位选项为每个控件。  
  
 如果你以编程方式添加 Windows 窗体控件，并提供范围自变量，该控件自动调整大小范围内的单元格调整大小时。 有关更多信息，请参见 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## <a name="resizing-controls-at-design-time"></a>在设计时调整控件的大小  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>若要使控件在设计时调整大小与单元格  
  
1.  从**工具箱**，将 Windows 窗体控件拖到工作表。  
  
2.  右击该控件，然后单击**格式控件**。  
  
3.  在**格式控件**对话框中，单击**属性**选项卡。  
  
4.  下**对象定位**，选择**移动并调整其大小与单元格**选项，并依次**确定**。  
  
     当您调整包含该控件的单元格时，控件将调整大小以适合该单元格。  
  
## <a name="resizing-controls-at-run-time"></a>在运行时调整控件的大小  
 如果你在运行时添加 Windows 窗体控件，并传入<xref:Microsoft.Office.Interop.Excel.Range>作为控件的位置，控件将自动调整大小，其中包含工作表单元格调整大小时。  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>若要使控件在运行时调整大小与单元格  
  
1.  将控件添加到范围 A1。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     当您调整包含该控件的单元格时，控件将调整大小以适合该单元格。  
  
## <a name="resetting-control-placement"></a>重置控件放置  
 你可以重置的位置和大小调整通过设置与控件`Placement`属性设置为以下项之一<xref:Microsoft.Office.Interop.Excel.XlPlacement>值：  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>若要更改控件的行为，以便不调整大小或移动与该单元格  
  
1.  调用控件的放置属性并将值设置为<xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>另请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [如何： 添加 Windows 窗体控件添加到 Office 文档](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何： 在打印时隐藏工作表上的控件](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office 文档上的 Windows 窗体控件限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  