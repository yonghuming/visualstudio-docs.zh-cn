---
title: "Chart 控件"
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
  - "VST.ProjectItem.ExcelChart"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "图表控件 [Visual Studio 中的 Office 开发]"
  - "图表控件 [Visual Studio 中的 Office 开发], 数据绑定"
  - "图表控件 [Visual Studio 中的 Office 开发], 事件"
ms.assetid: 64f1a7cc-cc66-47da-aaeb-44a62ae53909
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Chart 控件
  <xref:Microsoft.Office.Tools.Excel.Chart> 控件是公开事件的图表对象。  当将图表添加到工作表时，Visual Studio 将创建 <xref:Microsoft.Office.Tools.Excel.Chart> 对象，你可以直接针对此对象编程而无需遍历 Microsoft Office Excel 对象模型。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 创建控件  
 在文档级项目中，你可以在设计时或在运行时将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到 Microsoft Office Excel 工作表中。  
  
 在 VSTO 外接程序中，你可以在运行时将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到工作表中。  有关详细信息，请参阅[如何：向工作表添加 Chart 控件](../vsto/how-to-add-chart-controls-to-worksheets.md)。  
  
> [!NOTE]  
>  工作表关闭时，动态创建的图表控件不作为主机控件保留在工作表中。  有关详细信息，请参阅[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## 格式化  
 可应用于 <xref:Microsoft.Office.Interop.Excel.Chart> 的所有格式设置也可应用于 <xref:Microsoft.Office.Tools.Excel.Chart> 控件。  这包括边框、字体、图表类型、网格线、图例和数据标签。  
  
## 事件  
 以下事件可用于 <xref:Microsoft.Office.Tools.Excel.Chart> 控件：  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## 请参阅  
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何：向工作表添加 Chart 控件](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  