---
title: "XmlMappedRange 控件 |Microsoft 文档"
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
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 391964152c48601b11b10ce6d8001d2d303a9a01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange 控件
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控件是仅当非重复架构元素映射到 Microsoft Office Excel 中的单元格上时，才创建一个范围。 例如，当`maxOccurs`属性的架构元素等于 1。 Visual Studio 创建的映射的 XML 范围后，你可以对其编程直接而无需遍历 Excel 对象模型。 你只能删除<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>中 Excel 时元素映射将会删除控件。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何执行 i： 使用 XML 映射在 Excel 中？](http://go.microsoft.com/fwlink/?LinkID=130288)。  
  
## <a name="binding-data-to-the-control"></a>将数据绑定到控件  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控件支持绑定到单个数据字段 （简单数据绑定）。 <xref:Microsoft.Office.Tools.Excel.ListObject>控件可以支持复杂数据绑定，并将重复架构元素映射到单元格上时自动创建。 有关更多信息，请参见 [ListObject Control](../vsto/listobject-control.md)。  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控件绑定到数据源使用<xref:System.Windows.Forms.Control.DataBindings%2A>属性。 当<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Visual Studio 自动从映射的单元格中的数据生成数据集，并将控件绑定到该数据集添加到工作表单元格。 默认数据绑定属性<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>是<xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>。  
  
 如果在绑定数据集中的数据通过任何机制进行了更新<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控件会反映这些变化。  
  
## <a name="formatting"></a>格式设置  
 你可以应用相同的格式<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控件可以应用于<xref:Microsoft.Office.Interop.Excel.Range>。 这包括边框、字体、数字格式和样式。  
  
## <a name="events"></a>事件  
 可用于事件<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控件：  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>另请参阅  
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何： 向工作表添加 XMLMappedRange 控件](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何： 将架构映射到 Visual Studio 内部的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [主机项和主机控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  