---
title: "如何：以编程方式向文档中的文本添加注释 | Microsoft Docs"
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
  - "注释，添加到文档"
  - "文档 [Visual Studio 中的 Office 开发]，添加注释"
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：以编程方式向文档中的文本添加注释
  Document 类的 Comments 属性将向 Microsoft Office Word 文档中的某个文本范围添加注释。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下列示例将在文档中的第一个段落添加注释。  
  
### 向文档级自定义项中的文本添加新注释  
  
1.  调用 <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> 属性的 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 方法并提供范围和注释文本。 若要使用下面的代码示例，请从项目的 `ThisDocument` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomation#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#118)]  
  
### 向 VSTO 外接程序中的文本添加新注释  
  
1.  调用 <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> 属性的 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 方法并提供范围和注释文本。  
  
     下面的代码示例将向活动文档中添加注释。 若要使用此示例，请从项目的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#118)]  
  
## 可靠编程  
 若要更改 Word 在注释中添加的用户缩写，请使用 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> 属性。  
  
## 请参阅  
 [如何：以编程方式移除文档中的所有注释](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [文档宿主项](../vsto/document-host-item.md)  
  
  