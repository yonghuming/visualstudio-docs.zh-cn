---
title: "将数据绑定到 Office 解决方案中的控件 |Microsoft 文档"
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
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
ms.assetid: b6faaed7-df9b-4d78-9863-e515cd5c7ed9
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb94603d3041a30e978fff0ac6fff399648fc027
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="binding-data-to-controls-in-office-solutions"></a>将数据绑定到 Office 解决方案中的控件
  可以将 Microsoft Office Word 文档或 Microsoft Office Excel 工作表中的 Windows 窗体控件和 *宿主控件* 绑定到某个数据源，以便这些控件自动显示数据。 可以将数据绑定到应用程序级项目和文档级项目中的控件。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 宿主控件扩展 Word 和 Excel 对象模型中的对象，例如 Word 中的内容控件和 Excel 中的命名范围。 有关更多信息，请参见 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 Windows 窗体和宿主控件使用Windows 窗体数据绑定模型，该模型支持到数据源（例如数据集和数据表）的 *简单数据绑定* 和 *复杂数据绑定* 。 有关 Windows 窗体中的数据绑定模型的完整信息，请参阅[数据绑定和 Windows 窗体](/dotnet/framework/winforms/data-binding-and-windows-forms)。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何执行 i： 使用数据库数据在 Excel 中？](http://go.microsoft.com/fwlink/?LinkID=130287)。  
  
## <a name="simple-data-binding"></a>简单数据绑定  
 当控件属性绑定到单个数据元素（例如数据表中的值）时，即存在简单数据绑定。 例如， <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件中便有一个可以绑定到数据集中一个字段的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 属性。 当数据集中的字段发生更改时，命名范围中的值也会发生更改。 除 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件外，所有宿主控件都支持简单数据绑定。 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件是一个集合，因此不支持数据绑定。  
  
 若要执行到主机控件的简单数据绑定，请添加<xref:System.Windows.Forms.Binding>给控件的数据绑定属性。 <xref:System.Windows.Forms.Binding> 对象表示控件属性值和数据元素值之间的简单绑定。  
  
 下面的示例演示如何在文档级项目中将 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 属性绑定到数据元素。  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 有关演示简单数据绑定的演练，请参阅[演练： 文档级项目中的简单数据绑定](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)文档级别项目和[演练： 简单数据绑定，在 VSTO 外接程序项目](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) VSTO 外接程序项目。  
  
## <a name="complex-data-binding"></a>复杂数据绑定  
 当控件属性绑定到多个数据元素（例如数据表中的多个列）时，即存在复杂数据绑定。 Excel 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件是唯一支持复杂数据绑定的宿主控件。 此外，还有很多支持复杂数据绑定的 Windows 窗体控件，例如 <xref:System.Windows.Forms.DataGridView> 控件。  
  
 若要执行复杂数据绑定，请为复杂数据绑定支持的数据源对象设置控件的 DataSource 属性。 例如， <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> 控件的 <xref:Microsoft.Office.Tools.Excel.ListObject> 属性可以绑定到一个数据表中的多个列。 数据表中的所有数据都在 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件中显示，而当数据表中的数据发生更改时， <xref:Microsoft.Office.Tools.Excel.ListObject> 也会发生更改。 有关可用于复杂数据绑定的数据源的列表，请参阅 [Data Sources Supported by Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms)。  
  
 下面的代码示例创建具有两个 <xref:System.Data.DataSet> 对象的 <xref:System.Data.DataTable> ，并使用数据填充其中一个表。 代码随后将 <xref:Microsoft.Office.Tools.Excel.ListObject> 绑定到包含数据的表。 此示例适用于 Excel 文档级项目。  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 有关演示复杂数据绑定的演练，请参阅[演练： 文档级项目中的复杂数据绑定](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)文档级别项目和[演练： 复杂数据绑定，在 VSTO 外接程序项目](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) VSTO 外接程序项目。  
  
## <a name="displaying-data-in-documents-and-workbooks"></a>在文档和工作簿中显示数据  
 在文档级项目中，可通过与用于 Windows 窗体相同的方法，使用“数据源”  窗口轻松地将数据绑定控件添加到文档或工作簿中。 有关使用**数据源**窗口中，请参阅[绑定 Windows 窗体控件添加到 Visual Studio 中的数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)和[添加新数据源](../data-tools/add-new-data-sources.md)。  
  
### <a name="dragging-controls-from-the-data-sources-window"></a>从“数据源”窗口中拖动控件  
 从“数据源”  窗口中将一个对象拖到文档中时，会在此文档中创建一个控件。 所创建的控件的类型取决于绑定的是单列数据还是多列数据。  
  
 对于 Excel，会在工作表上为每个单独的字段创建一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，并且会为每个包括多个行和列的数据范围创建一个 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。 通过在“数据源”  窗口中选择表或字段，然后从下拉列表中选择其他控件，可以更改此默认设置。  
  
 <xref:Microsoft.Office.Tools.Word.ContentControl> 控件即会添加到文档中。 内容控件的类型取决于所选字段的数据类型。  
  
### <a name="binding-data-in-document-level-projects-at-design-time"></a>在文档级项目中在设计时绑定数据  
 下面的主题介绍在设计时绑定数据的示例：  
  
-   [如何：用数据库中的数据填充工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [如何：用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [如何：用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [如何：用服务中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [如何：在工作表中滚动查看数据库记录](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="binding-data-in-vsto-add-in-projects"></a>在 VSTO 外接程序项目中绑定数据  
 在 VSTO 外接程序项目中，仅可在运行时添加控件。 下面的主题介绍在运行时绑定数据的示例：  
  
-   [演练：VSTO 外接程序项目中的简单数据绑定](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [演练：VSTO 外接程序项目中的复杂数据绑定](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="updating-data-that-is-bound-to-host-controls"></a>更新绑定到宿主控件的数据  
 在数据源和宿主控件之间进行数据绑定会涉及到双向数据更新。 在简单数据绑定中，数据源中所做的更改会在宿主控件中自动反映，但宿主控件中所做的更改则需要通过显式调用才能更新数据源。 原因是，在某些情况下，如果只更改一个数据绑定字段而没有相应地更改另一个数据绑定字段，则不会接受对该数据绑定字段所做的更改。 例如，假定有两个字段，一个是年龄字段，另一个是工作经验字段。 工作经验值不可能比年龄值大。 用户不能将年龄字段从 50 更新为 25，然后再将工作经验字段从 30 更新为 10，而只能同时对这两个字段做相应更改。 若要解决此问题，只有通过代码来显式发送更新，才能对简单数据绑定字段进行更新。  
  
 若要从支持简单数据绑定的宿主控件更新数据源，则必须将更新发送到内存中数据源（例如 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable>）和后端数据库（如果你的解决方案使用后端数据库）。  
  
 如果使用 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件执行复杂数据绑定，则无需显式更新内存中数据源。 在这种情况下，无需其他代码，更改即会自动发送到内存中数据源。  
  
 有关详细信息，请参阅 [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何实现：在 Excel 中使用数据库数据？](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [数据绑定和 Windows 窗体](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [如何：在 Windows 窗体上创建简单绑定控件](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)    
 [使用 TableAdapter 更新数据](../data-tools/update-data-by-using-a-tableadapter.md)    
 [缓存数据](../vsto/caching-data.md)   
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)  
  
  