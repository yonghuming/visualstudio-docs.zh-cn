---
title: "如何：以编程方式在文档中设置文本格式 | Microsoft Docs"
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
  - "格式设置 [Visual Studio 中的 Office 开发]"
  - "文档 [Visual Studio 中的 Office 开发]，设置文本格式"
  - "文本 [Visual Studio 中的 Office 开发]，在文档中设置格式"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 如何：以编程方式在文档中设置文本格式
  你可以使用 <xref:Microsoft.Office.Interop.Word.Range> 对象来格式化 Microsoft Office Word 文档中的文本。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下面的示例选择文档中的第一个段落并更改字号、字体名称和对齐方式。 然后，它会选择范围并显示一个消息框，以在执行下一段代码前暂停。 下一部分会调用 <xref:Microsoft.Office.Tools.Word.Document> 主机项（对于文档级自定义项）或 <xref:Microsoft.Office.Interop.Word.Document> 类（对于 VSTO 外接程序）的 Undo 方法三次。 它应用“正文缩进”样式，并显示一个消息框以暂停代码。 然后，该代码调用 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> 方法一次，并显示一个消息框。  
  
## 文档级自定义项示例  
  
#### 使用文档级自定义项格式化文本  
  
1.  可以在文档级自定义项中使用下面的示例。 若要使用此代码，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## VSTO 外接程序示例  
  
#### 使用 VSTO 外接程序格式化文本  
  
1.  可以在 VSTO 外接程序中使用下面的示例。 本示例使用活动文档。 若要使用此代码，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## 请参阅  
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以编程方式在 Word 文档中插入文本](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以编程方式在文档中搜索和替换文本](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  