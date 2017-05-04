---
title: "如何：以编程方式更新书签文本 | Microsoft Docs"
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
  - "Bookmark 控件, 更新内容"
  - "书签, 更新文本"
  - "文本 [Visual Studio 中的 Office 开发], 在书签中更新"
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以编程方式更新书签文本
  你可以将文本插入 Microsoft Office Word 文档中的占位符书签，以便稍后能够检索到该文本，或替换书签中的文本。  如果你正在开发文档级自定义项，则还可以更新绑定到数据的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件中的文本。  有关详细信息，请参阅[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 书签对象可为以下两种类型之一：  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark> 主机控件。  
  
     <xref:Microsoft.Office.Tools.Word.Bookmark> 控件会通过启用数据绑定和公开事件来扩展本机 <xref:Microsoft.Office.Interop.Word.Bookmark> 对象。  有关主机控件的详细信息，请参阅[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
-   本机 <xref:Microsoft.Office.Interop.Word.Bookmark> 对象。  
  
     <xref:Microsoft.Office.Interop.Word.Bookmark> 对象没有事件或数据绑定功能。  
  
 将文本分配到书签时，<xref:Microsoft.Office.Interop.Word.Bookmark> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 的行为有所不同。  有关详细信息，请参阅[Bookmark 控件](../vsto/bookmark-control.md)。  
  
## 使用主机控件  
  
#### 使用书签控件更新书签内容  
  
1.  创建一个过程，它将 `bookmark` 参数用作书签的名称，并将 `newText` 参数用作要分配给 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 属性的字符串。  
  
    > [!NOTE]  
    >  将文本分配给 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件的 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 或 <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> 属性不会删除书签。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#63)]
     [!code-vb[Trin_VstcoreWordAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#63)]  
  
2.  将 *newText* 字符串分配给 <xref:Microsoft.Office.Tools.Word.Bookmark> 的 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 属性。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#64)]
     [!code-vb[Trin_VstcoreWordAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#64)]  
  
## 使用 Word 对象  
  
#### 使用 Word 书签对象更新书签内容  
  
1.  创建一个过程，它将 `bookmark` 参数用作 <xref:Microsoft.Office.Interop.Word.Bookmark> 的名称，并将 `newText` 参数用作要分配给书签的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 属性的字符串。  
  
    > [!NOTE]  
    >  将文本分配给本机 Word <xref:Microsoft.Office.Interop.Word.Bookmark> 对象会造成书签被删除。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#65)]
     [!code-vb[Trin_VstcoreWordAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#65)]  
  
2.  将 *newText* 字符串分配给书签的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 属性，这会自动删除该书签。  然后将书签重新添加到 <xref:Microsoft.Office.Interop.Word.Bookmarks> 集合。  
  
     下面的代码示例可用于文档级自定义项。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#66)]  
  
     以下代码示例可用于 VSTO 外接程序。  本示例使用活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#66)]  
  
## 请参阅  
 [如何：以编程方式在 Word 文档中插入文本](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [Bookmark 控件](../vsto/bookmark-control.md)  
  
  