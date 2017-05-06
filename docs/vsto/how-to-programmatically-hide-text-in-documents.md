---
title: "如何：以编程方式隐藏文档中的文本"
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
  - "文档 [Visual Studio 中的 Office 开发]，隐藏文本"
  - "文本 [Visual Studio 中的 Office 开发]，隐藏在文档中"
ms.assetid: f5ced4ec-22ca-463b-b963-d34ce631b486
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：以编程方式隐藏文档中的文本
  通过将 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 属性设置为某个特定范围文本的 <xref:Microsoft.Office.Interop.Word.Range.Font%2A>。  
  
 例如，在将文档发送到打印机之前，你可以暂时将文本隐藏在 <xref:Microsoft.Office.Tools.Word.Bookmark>（文档级自定义项中）或 <xref:Microsoft.Office.Interop.Word.Bookmark>（VSTO 外接程序中）。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 打印文档时在 Bookmark 控件中隐藏文本  
  
1.  创建一个过程，它会隐藏特定范围内的所有文本。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#105](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#105)]
     [!code-vb[Trin_VstcoreWordAutomation#105](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#105)]  
  
2.  创建一个过程，它会取消隐藏特定范围内的所有文本。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#106](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#106)]
     [!code-vb[Trin_VstcoreWordAutomation#106](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#106)]  
  
3.  将书签的范围传递到 `HideText` 方法，打印文档，然后将相同范围传递到 `UnhideText` 方法。  
  
     下面的代码示例可用于文档级自定义项。 若要使用此示例，请从项目的 `ThisDocument` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomation#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#107)]  
  
     以下代码示例可用于 VSTO 外接程序。 本示例使用活动文档。 若要使用此示例，请从项目的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#107)]  
  
## 编译代码  
 此代码示例假定文档包含一个 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件（在文档级自定义项中）或名为 `bookmark1` 的 <xref:Microsoft.Office.Interop.Word.Bookmark> 控件（在 VSTO 外接程序中）。  
  
## 请参阅  
 [如何：以编程方式打印文档](../vsto/how-to-programmatically-print-documents.md)   
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以编程方式重置 Word 文档中的范围](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以编程方式更新书签文本](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  