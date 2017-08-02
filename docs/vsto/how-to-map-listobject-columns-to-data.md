---
title: "如何：将 ListObject 列映射到数据"
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
  - "数据 [Visual Studio 中的 Office 开发]，映射到 ListObject 列"
  - "ListObject 控件，映射数据"
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 如何：将 ListObject 列映射到数据
  将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件绑定到 <xref:System.Data.DataTable> 时，可能不希望显示列表中的所有列，或可能具有未绑定到数据的特定列。 调用 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法时，可以映射希望出现在 <xref:Microsoft.Office.Tools.Excel.ListObject> 中的列。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![链接到视频](~/docs/data-tools/media/playvideo.gif "链接到视频") 相关视频演示，请参阅[如何：在 Excel 中创建连接到 SharePoint 列表的列表](http://go.microsoft.com/fwlink/?LinkID=130263)。  
  
## 映射列  
  
#### 将数据表映射到列表中的列  
  
1.  在类级创建 <xref:System.Data.DataTable>。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#16)]  
  
2.  在 `Sheet1` 类（文档级项目中）或 `ThisAddIn` 类（VSTO 外接程序项目中）的 `Startup` 事件处理程序中添加示例列和数据。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#17)]  
  
3.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法并以列名应显示的顺序传入列表。 列表对象会绑定到新创建的 <xref:System.Data.DataTable>，但列表对象中列的顺序会与它们在 <xref:System.Data.DataTable> 中出现的顺序不同。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#18)]  
  
## 指定未映射的列  
 将列映射到 <xref:System.Data.DataTable> 时，还可以通过传入空字符串来指定特定列不应绑定到数据。 未绑定到数据的新列随后会添加到 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  
  
#### 在映射 ListObject 列时指定未映射的列  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法并以列名应显示的顺序传入列表。 使用空字符串可指示添加未映射的列的位置；在此例中，是介于标题.栏与最后一个名称列之间。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#19)]  
  
## 编译代码  
 此代码示例假定在此代码出现的工作表中有一个名为 `list1` 的现有 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
## 请参阅  
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：用数据填充 ListObject 控件](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控件](../vsto/listobject-control.md)  
  
  