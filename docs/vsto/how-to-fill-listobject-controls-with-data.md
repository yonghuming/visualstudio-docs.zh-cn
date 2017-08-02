---
title: "如何：用数据填充 ListObject 控件"
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
  - "与数据源断开连接"
  - "ListObject 控件，断开与数据源的连接"
  - "ListObject 控件，使用数据填写"
  - "数据 [Visual Studio 中的 Office 开发]，添加到工作表"
  - "数据绑定，ListObject 控件"
  - "工作表，使用数据填充"
ms.assetid: bf692c77-f5cc-456a-9a5c-84ed3067d7eb
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：用数据填充 ListObject 控件
  可以使用数据绑定快速地将数据添加到文档中。 将数据绑定到列表对象后，可以断开列表对象的连接，以便它能显示数据且不再与数据源绑定。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![链接到视频](~/docs/data-tools/media/playvideo.gif "链接到视频") 相关视频演示，请参阅[如何：在 Excel 中创建连接到 SharePoint 列表的列表](http://go.microsoft.com/fwlink/?LinkID=130263)。  
  
### 将数据绑定到 ListObject 控件  
  
1.  在类级创建 <xref:System.Data.DataTable>。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#20)]  
  
2.  在 `Sheet1` 类（文档级项目中）或 `ThisAddIn` 类（应用程序级项目中）的 `Startup` 事件处理程序中添加示例列和数据。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#21)]  
  
3.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法并以列名应显示的顺序传入列表。 列表对象中的列顺序可能与 <xref:System.Data.DataTable> 中显示的列顺序不同。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#22)]  
  
### 若要断开 ListObject 控件与数据源的连接  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> 的 `List1` 方法。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#23)]  
  
## 编译代码  
 此代码示例假定在此代码出现的工作表中有一个名为 `list1` 的现有 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
## 请参阅  
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：将 ListObject 列映射到数据](../vsto/how-to-map-listobject-columns-to-data.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控件](../vsto/listobject-control.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：用数据库中的数据填充工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何：用服务中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  