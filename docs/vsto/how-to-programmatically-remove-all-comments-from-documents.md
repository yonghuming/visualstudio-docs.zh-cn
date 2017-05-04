---
title: "如何：以编程方式移除文档中的所有注释 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发]，删除注释"
  - "注释，从文档中删除"
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：以编程方式移除文档中的所有注释
  使用 DeleteAllComments 方法可以删除 Microsoft Office Word 文档中的所有注释。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 从属于文档级自定义项的文档中删除所有注释  
  
1.  调用项目中 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> 方法。 若要使用此代码示例，请从 `ThisDocument` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomation#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#119)]  
  
### 使用 VSTO 外接程序从文档中删除所有注释  
  
1.  调用要从中删除注释的 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> 方法。  
  
     下面的代码示例从活动文档中删除所有注释。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#119)]  
  
## 请参阅  
 [如何：以编程方式向文档中的文本添加注释](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [文档宿主项](../vsto/document-host-item.md)  
  
  