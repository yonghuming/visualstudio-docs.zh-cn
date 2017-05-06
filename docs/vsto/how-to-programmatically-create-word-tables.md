---
title: "如何：以编程方式创建 Word 表"
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
  - "文档 [Visual Studio 中的 Office 开发], 添加表"
  - "表 [Visual Studio 中的 Office 开发], 添加到文档"
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 如何：以编程方式创建 Word 表
  <xref:Microsoft.Office.Interop.Word.Tables> 集合是 <xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Interop.Word.Selection> 和 <xref:Microsoft.Office.Interop.Word.Range> 类的成员，这意味着可以在上述任一上下文中创建表格。  使用 <xref:Microsoft.Office.Interop.Word.Tables> 集合的 <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 方法在指定范围内添加表格。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 在文档级自定义项中创建表格  
  
#### 向文档添加简单表格  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 方法在文档开头添加一个三行四列的表格。  
  
     若要使用下面的代码示例，请从项目的 `ThisDocument` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomation#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#86)]  
  
 在创建表格时，表格会自动添加到 <xref:Microsoft.Office.Tools.Word.Document> 主机项的 <xref:Microsoft.Office.Interop.Word.Tables> 集合中。  然后，可以使用 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 属性按照项编号引用该表格，如以下代码所示。  
  
#### 按照项编号引用表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 属性并提供要引用的表格的项编号。  
  
     若要使用下面的代码示例，请从项目的 `ThisDocument` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomation#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#87)]  
  
 每个 <xref:Microsoft.Office.Interop.Word.Table> 对象还具有一个 <xref:Microsoft.Office.Interop.Word.Table.Range%2A> 属性，该属性可用于设置格式属性。  
  
#### 将样式应用到表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Table.Style%2A> 属性将其中一个 Word 内置样式应用到表格。  
  
     若要使用下面的代码示例，请从项目的 `ThisDocument` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomation#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#88)]  
  
## 在 VSTO 外接程序中创建表格  
  
#### 向文档添加简单表格  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 方法在文档开头添加一个三行四列的表格。  
  
     下面的代码示例是向活动文档添加一个表格。  若要使用此示例，请从项目的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#86)]  
  
 在创建表格时，表格会自动添加到 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word.Tables> 集合中。  然后，可以使用 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 属性按照项编号引用该表格，如以下代码所示。  
  
#### 按照项编号引用表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 属性并提供要引用的表格的项编号。  
  
     下面的代码示例使用活动文档。  若要使用此示例，请从项目的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#87)]  
  
 每个 <xref:Microsoft.Office.Interop.Word.Table> 对象还具有一个 <xref:Microsoft.Office.Interop.Word.Table.Range%2A> 属性，该属性可用于设置格式属性。  
  
#### 将样式应用到表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Table.Style%2A> 属性将其中一个 Word 内置样式应用到表格。  
  
     下面的代码示例使用活动文档。  若要使用此示例，请从项目的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#88)]  
  
## 请参阅  
 [如何：以编程方式向 Word 表中的单元格添加文本和格式设置](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [如何：以编程方式向 Word 表中添加行和列](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [如何：以编程方式用文档属性填充 Word 表](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  