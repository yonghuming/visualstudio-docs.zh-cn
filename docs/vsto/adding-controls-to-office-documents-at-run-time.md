---
title: "在运行时向 Office 文档添加控件 |Microsoft 文档"
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
ms.assetid: 4f43b3eb-f0ec-44e2-9885-6ede327c6913
caps.latest.revision: "102"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: db8a4fad73bb710662ce63bd299751c725e0c6ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-controls-to-office-documents-at-run-time"></a>在运行时向 Office 文档添加控件
  可以在运行时向 Microsoft Office Word 文档和 Microsoft Office Excel 工作簿中添加控件。 还可以在运行时删除这些控件。 在运行时添加或删除的控件称为 *动态控件*。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 本主题介绍了以下任务：  
  
-   [使用控件集合在运行时管理控件](#ControlsCollection)。  
  
-   [向文档中添加宿主控件](#HostControls)。  
  
-   [向文档中添加 Windows 窗体控件](#WindowsForms)。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何执行 i： 将控件添加到文档图面在运行时？](http://go.microsoft.com/fwlink/?LinkId=132782)。  
  
##  <a name="ControlsCollection"></a> Managing Controls at Run Time by Using the Control Collections  
 若要在运行时添加、获取或删除控件，请使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 和 <xref:Microsoft.Office.Tools.Word.ControlCollection> 对象的帮助器方法。  
  
 访问这些对象的方式取决于所开发项目的类型：  
  
-   在 Excel 文档级项目中，使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 、 `Sheet1`和 `Sheet2`类的 `Sheet3` 属性。 有关这些类的详细信息，请参阅[工作表主机项](../vsto/worksheet-host-item.md)。  
  
-   在 Word 文档级项目中，使用 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 类的 `ThisDocument` 属性。 有关此类的详细信息，请参阅[文档主机项](../vsto/document-host-item.md)。  
  
-   在 Excel 或 Word 的 VSTO 外接程序项目，使用的控件属性<xref:Microsoft.Office.Tools.Excel.Worksheet>或<xref:Microsoft.Office.Tools.Word.Document>在运行时生成。 有关在运行时生成这些对象的详细信息，请参阅[扩展 Word 文档和 Excel VSTO 外接程序在运行时中的工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### <a name="adding-controls"></a>添加控件  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 和 <xref:Microsoft.Office.Tools.Word.ControlCollection> 类型包含可用于将宿主控件和公共 Windows 窗体控件添加到文档和工作表中的帮助器方法。 每个方法名的格式均为 `Add`*control class*，其中 *control class* 是所要添加的控件的类名称。 例如，若要向文档中添加 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，请使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> 方法。  
  
 下面的代码示例会在 Excel 文档级项目中将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 添加到 `Sheet1` 中。  
  
 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  
  
### <a name="accessing-and-deleting-controls"></a>访问和删除控件  
 你可以使用的控件属性<xref:Microsoft.Office.Tools.Excel.Worksheet>或<xref:Microsoft.Office.Tools.Word.Document>来循环访问您的文档，包括在设计时添加的控件中的所有控件。 在设计时添加的控件也称为 *静态控件*。  
  
 通过调用 Delete 方法的控件，或通过调用删除方法的每个控件集合，你可以删除动态控件。 以下代码示例使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> 方法在 Excel 文档级项目中从 <xref:Microsoft.Office.Tools.Excel.NamedRange> 中删除 `Sheet1` 。  
  
 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  
  
 不能在运行时删除静态控件。 如果你尝试删除或删除方法用于删除静态控件，<xref:Microsoft.Office.Tools.CannotRemoveControlException>将引发。  
  
> [!NOTE]  
>  请不要以编程方式在文档的 `Shutdown` 事件处理程序中删除控件。 发生 `Shutdown` 事件时，文档的 UI 元素将不再可用。 如果要在关闭文档之前删除控件，请将你的代码添加到另一个事件的事件处理程序中，对于 Word 为 <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> 或 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> ，对于 Excel 为 <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>或 <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> 。  
  
##  <a name="HostControls"></a> Adding Host Controls to Documents  
 当以编程方式向文档中添加宿主控件时，必须提供一个可唯一标识该控件的名称，并且指定要将控件添加到文档中的位置。 有关具体说明，请参阅以下主题：  
  
-   [如何：将 ListObject 控件添加到工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [如何：将 NamedRange 控件添加到工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [如何：将 Chart 控件添加到工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [如何：将内容控件添加到 Word 文档](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [如何：将书签控件添加到 Word 文档](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
 有关宿主控件的详细信息，请参阅 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 保存并关闭文档后，动态创建的宿主控件会断开与其事件的连接，并丧失其数据绑定功能。 可以向解决方案中添加代码，以在重新打开文档时重新创建这些宿主控件。 有关更多信息，请参见 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
> [!NOTE]  
>  以下宿主控件不具备帮助器方法，因为不能以编程方式将这些控件添加到 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、 <xref:Microsoft.Office.Tools.Word.XMLNode>和 <xref:Microsoft.Office.Tools.Word.XMLNodes>文档中。  
  
##  <a name="WindowsForms"></a> Adding Windows Forms Controls to Documents  
 当以编程方式向文档中添加 Windows 窗体控件时，必须提供控件的位置和一个可唯一标识该控件的名称。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 为每个控件提供帮助器方法。 这些方法将重载，以便可以传递控件位置的范围或具体坐标。  
  
 保存并关闭文档后，会自动从文档中删除所有动态创建的 Windows 窗体控件。 可以向解决方案中添加代码，以在重新打开文档时重新创建这些控件。 如果使用 VSTO 外接程序创建动态 Windows 窗体控件，则控件的 ActiveX 包装会保留在文档中。 有关更多信息，请参见 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
> [!NOTE]  
>  不能以编程方式向受保护的文档添加 Windows 窗体控件。 如果通过以编程方式取消 Word 文档或 Excel 工作表保护来添加控件，则必须编写额外的代码在关闭文档时删除该控件的 ActiveX 包装。 该控件的 ActiveX 包装不会从受保护的文档中自动删除。  
  
### <a name="adding-custom-controls"></a>添加自定义控件  
 如果想要添加可用帮助器方法不支持的 <xref:System.Windows.Forms.Control> （如自定义用户控件），请使用以下方法：  
  
-   对于 Excel，使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> 对象的 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 方法。  
  
-   对于 Word，使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> 对象的 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法。  
  
 若要添加控件，请将传递<xref:System.Windows.Forms.Control>、 该控件的位置和唯一标识该控件到 AddControl 方法的名称。 AddControl 方法返回定义控件如何与工作表或文档交互的对象。 AddControl 方法返回<xref:Microsoft.Office.Tools.Excel.ControlSite>（针对 Excel) 或<xref:Microsoft.Office.Tools.Word.ControlSite>对象 （针对 Word)。  
  
 以下代码示例演示了如何使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> 方法将自定义用户控件动态添加到文档级 Excel 项目的工作表中。 在此示例中，用户控件名为 `UserControl1`， <xref:Microsoft.Office.Interop.Excel.Range> 名为 `range1`。 若要使用此示例，请从项目的 `Sheet`*n* 类中运行。  
  
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  
  
### <a name="using-members-of-custom-controls"></a>使用自定义控件的成员  
 使用后 AddControl 方法之一将控件添加到工作表或文档，现在有两个不同的控件对象：  
  
-   <xref:System.Windows.Forms.Control> 表示自定义控件。  
  
-   ControlSite、 OLEObject 或 OLEControl 对象，它表示控件添加到工作表或文档。  
  
 这些控件之间共享多个属性和方法。 必须通过适当的控件访问这些成员：  
  
-   若要访问仅属于自定义控件的成员，请使用 <xref:System.Windows.Forms.Control>。  
  
-   若要访问由这些控件共享的成员，请使用 ControlSite、 OLEObject 或 OLEControl 对象。  
  
 如果访问 <xref:System.Windows.Forms.Control>中的共享成员，可能会失败，同时不发出任何警告或通知，也可能会产生无效的结果。 始终使用 ControlSite、 OLEObject 或 OLEControl 对象的方法或属性，除非方法或所需属性不可用;只有在那时应引用<xref:System.Windows.Forms.Control>。  
  
 例如，<xref:Microsoft.Office.Tools.Excel.ControlSite>类和<xref:System.Windows.Forms.Control>类具有 Top 属性。 若要获取或设置控件顶部和文档开头之间的距离，请使用 <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> 的 <xref:Microsoft.Office.Tools.Excel.ControlSite>属性，而不是 <xref:System.Windows.Forms.Control.Top%2A> 的 <xref:System.Windows.Forms.Control>属性。  
  
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  
  
## <a name="see-also"></a>另请参阅  
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在 Office 文档中保留动态控件](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [如何： 向工作表添加 ListObject 控件](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何： 向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [如何： 向工作表添加图表控件](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [如何： 向 Word 文档添加内容控件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Windows 窗体上的控件 Office 文档概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [如何：将 Windows 窗体控件添加到 Office 文档](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
