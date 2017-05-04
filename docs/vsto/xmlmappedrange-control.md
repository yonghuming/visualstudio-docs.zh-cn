---
title: "XmlMappedRange 控件 | Microsoft Docs"
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
  - "XMLMappedRange 控件"
  - "XMLMappedRange 控件, 数据绑定"
  - "XMLMappedRange 控件, 事件"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# XmlMappedRange 控件
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件是一个范围，只有当非重复架构元素映射到 Microsoft Office Excel 中的单元格上时，才会创建该范围。  例如，当架构元素的 `maxOccurs` 特性等于 1 时。  在 Visual Studio 创建了 XML 映射范围后，您可以直接依据该范围进行编程，而不必遍历 Excel 对象模型。  只有元素映射被移除后，才能删除 Excel 内的 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![链接到视频](../vsto/media/playvideo.png "链接到视频") 有关相关视频演示，请参见 [How Do I: Use XML Mapping in Excel?](http://go.microsoft.com/fwlink/?LinkID=130288)（如何实现：在 Excel 中使用 XML 映射？）。  
  
## 将数据绑定到控件  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件支持绑定到单个数据字段（简单数据绑定）。  <xref:Microsoft.Office.Tools.Excel.ListObject> 控件可以支持复杂数据绑定，此控件在重复架构元素映射到单元格上时自动被创建。  有关更多信息，请参见[ListObject 控件](../vsto/listobject-control.md)。  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件使用 <xref:System.Windows.Forms.Control.DataBindings%2A> 属性绑定到数据源。  当将 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 添加到工作表单元格时，Visual Studio 将自动依据映射的单元格中的数据生成数据集，并将此控件绑定到该数据集。  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 的默认数据绑定属性为 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>。  
  
 如果绑定数据集内的数据通过任何机制被更新，<xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件就会反映出所做的更改。  
  
## 格式设置  
 可以将与可应用于 <xref:Microsoft.Office.Interop.Excel.Range> 的格式设置相同的格式设置应用于 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件。  这包括边框、字体、数字格式和样式。  
  
## 事件  
 对于 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件可用的事件有：  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## 请参阅  
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何：向工作表添加 XMLMappedRange 控件](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：将架构映射到 Visual Studio 内部的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  