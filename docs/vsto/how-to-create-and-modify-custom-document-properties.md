---
title: "如何：创建和修改自定义文档属性"
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
  - "自定义文档属性"
  - "文档 [Visual Studio 中的 Office 开发]，属性"
  - "文档属性 [Visual Studio 中的 Office 开发]"
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：创建和修改自定义文档属性
  上面列出的 Microsoft Office 应用程序提供与文档存储在一起的内置属性。 此外，如果要将其他信息与文档一起存储，可以创建和修改自定义文档属性。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 将文档的 CustomDocumentProperties 属性与自定义属性一起使用。 例如，在 Microsoft Office Excel 的文档级项目中，请使用 `ThisWorkbook` 类的 <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> 属性。 在 Excel 的 VSTO 外接程序项目中，请使用 <xref:Microsoft.Office.Interop.Excel.Workbook> 对象的 <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> 属性。 这些属性将返回 <xref:Microsoft.Office.Core.DocumentProperties> 对象，该对象为 <xref:Microsoft.Office.Core.DocumentProperty> 对象的集合。 可以使用集合的 `Item` 属性，按名称或索引检索该集合中的特定属性。  
  
 下面的示例演示如何在 Excel 文档级自定义项中添加自定义属性并为其赋值。  
  
 ![链接到视频](~/docs/data-tools/media/playvideo.gif "链接到视频") 相关视频演示，请参阅[如何实现：在 Microsoft Word 中访问和操作自定义文档属性？](http://go.microsoft.com/fwlink/?LinkId=136772)。  
  
## 示例  
 [!code-csharp[Trin_VstcoreProgramming#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#6)]
 [!code-vb[Trin_VstcoreProgramming#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#6)]  
  
## 可靠编程  
 尝试访问未定义的属性的 `Value` 属性会引发异常。  
  
## 请参阅  
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)   
 [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)   
 [如何：从文档属性中读取或向文档属性写入](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  