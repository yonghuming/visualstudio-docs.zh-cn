---
title: "NamedRange 控件"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Toolbox.Range"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "范围，已命名"
  - "NamedRange 控件，事件"
  - "NamedRange 控件，数据绑定"
  - "NamedRange 控件"
ms.assetid: 07878c7c-cb5a-4f98-95c4-e828de25dae5
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# NamedRange 控件
  <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件是一个具有唯一名称的范围，可用于公开事件且可以绑定到数据。 有关详细信息，请参阅[Excel 对象模型概述](../vsto/excel-object-model-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 创建控件  
 在文档级项目中，你可以在设计时或在运行时将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件添加到 Microsoft Office Excel 工作表中。  
  
 在 VSTO 外接程序中，你可以在运行时将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件添加到工作表中。 有关详细信息，请参阅[如何：向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)。  
  
> [!NOTE]  
>  默认情况下，工作表关闭时，动态创建的命名范围不作为宿主控件保留在工作表中。 有关更多信息，请参见[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件可以仅包含特定的工作表上的范围。<xref:Microsoft.Office.Tools.Excel.NamedRange> 控件不能具有适用于所有表的相对名称并且它们不能包含跨越工作簿中的两个或多个工作表的范围（3\-D 范围）。  
  
## 将数据绑定到控件  
 命名的区域似乎很适合复杂的数据绑定，因为它可以有多个单元格；但是，范围仅仅是单元格的集合，无法轻易地从数据集映射到特定列。 因此，<xref:Microsoft.Office.Tools.Excel.NamedRange> 控件仅支持简单数据绑定。<xref:Microsoft.Office.Tools.Excel.ListObject> 控件可用于复杂数据绑定。 有关更多信息，请参见[ListObject 控件](../vsto/listobject-control.md)。  
  
 可以使用 <xref:System.Windows.Forms.Control.DataBindings%2A> 属性将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件绑定到数据源。<xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的默认数据绑定属性是 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>。  
  
 如果绑定数据集中的数据通过任何机制进行了更新，那么 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件会反映这些变化。  
  
## 格式设置  
 可应用于 <xref:Microsoft.Office.Interop.Excel.Range> 的格式设置也可应用于 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。 这包括边框、字体、数字格式和样式。  
  
## 重命名控件  
 当你将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件从“工具箱”添加到工作表时，Visual Studio 会自动生成该控件的名称。 你可以在“属性”窗口中更改名称。  
  
## 事件  
 以下事件可用于 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件：  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## 请参阅  
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [如何：调整 NamedRange 控件的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [演练：根据 NamedRange 控件的事件进行编程](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  