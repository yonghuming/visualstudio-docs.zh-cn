---
title: "如何： 将 ListObject 列映射到数据 |Microsoft 文档"
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
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bda2e6626e7d636fd4c53ed3ddbb5cfadc42666f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-map-listobject-columns-to-data"></a>如何：将 ListObject 列映射到数据
  将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件绑定到 <xref:System.Data.DataTable>时，可能不希望显示列表中的所有列，或可能具有未绑定到数据的特定列。 调用 <xref:Microsoft.Office.Tools.Excel.ListObject> 方法时，可以映射希望出现在 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 中的列。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何： 创建列表在连接到 SharePoint 列表的 Excel 中？](http://go.microsoft.com/fwlink/?LinkID=130263)。  
  
## <a name="mapping-columns"></a>映射列  
  
#### <a name="to-map-a-data-table-to-columns-in-a-list"></a>将数据表映射到列表中的列  
  
1.  在类级创建 <xref:System.Data.DataTable> 。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  在 `Startup` 类（文档级项目中）或 `Sheet1` 类（VSTO 外接程序项目中）的 `ThisAddIn` 事件处理程序中添加示例列和数据。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法并以列名应显示的顺序传入列表。 列表对象会绑定到新创建的 <xref:System.Data.DataTable>，但列表对象中列的顺序会与它们在 <xref:System.Data.DataTable>中出现的顺序不同。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specifying-unmapped-columns"></a>指定未映射的列  
 将列映射到 <xref:System.Data.DataTable>时，还可以通过传入空字符串来指定特定列不应绑定到数据。 未绑定到数据的新列随后会添加到 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  
  
#### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>在映射 ListObject 列时指定未映射的列  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法并以列名应显示的顺序传入列表。 使用空字符串可指示添加未映射的列的位置；在此例中，是介于标题.栏与最后一个名称列之间。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此代码示例假定在此代码出现的工作表中有一个名为 <xref:Microsoft.Office.Tools.Excel.ListObject> 的现有 `list1` 。  
  
## <a name="see-also"></a>另请参阅  
 [在运行时扩展 Word 文档和 Excel 工作簿在 VSTO 外接程序](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何： 用数据填充 ListObject 控件](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控件](../vsto/listobject-control.md)  
  
  