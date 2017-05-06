---
title: "如何：以编程方式向 Word 表中的单元格添加文本和格式设置"
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
  - "单元格, 添加文本和格式"
  - "格式设置 [Visual Studio 中的 Office 开发]"
  - "表 [Visual Studio 中的 Office 开发], 添加文本和格式"
  - "文本 [Visual Studio 中的 Office 开发], 添加到 Word 表"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：以编程方式向 Word 表中的单元格添加文本和格式设置
  每个表都包含一个单元格集合。  每个单独的 <xref:Microsoft.Office.Interop.Word.Cell> 对象都表示表中的一个单元格。  你可以通过表中每个单元格的位置对其进行引用。  此示例引用位于表中第一行和第一列的单元格；将文本添加到单元格；并应用格式设置。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 若要将文本和格式设置添加到单元格  
  
1.  通过单元格在表中的位置对其进行引用，将文本添加到单元，并应用格式设置。  
  
     下面的代码示例可用于文档级自定义项。  若要使用此示例，请从项目的 `ThisDocument` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     以下代码示例可用于 VSTO 外接程序。  本示例使用活动文档。  若要使用此示例，请从项目的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## 请参阅  
 [如何：以编程方式创建 Word 表](../vsto/how-to-programmatically-create-word-tables.md)   
 [如何：以编程方式向 Word 表中添加行和列](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [如何：以编程方式用文档属性填充 Word 表](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  