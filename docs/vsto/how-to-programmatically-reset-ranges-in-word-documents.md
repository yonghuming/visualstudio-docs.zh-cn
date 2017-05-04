---
title: "如何：以编程方式重置 Word 文档中的范围 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发]，重置范围"
  - "范围，在文档中重置"
ms.assetid: 45ea9434-e548-4d24-938f-4f1ffa5010d0
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：以编程方式重置 Word 文档中的范围
  使用 <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> 方法在 Microsoft Office Word 文档中调整现有范围的大小。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 重置现有范围  
  
1.  设置从文档中的前七个字符开始的初始范围。  
  
     下面的代码示例可用于文档级自定义项。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#43)]  
  
     以下代码示例可用于 VSTO 外接程序。 此代码运用了活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#43)]  
  
2.  使用 <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> 设置第二个句子为范围的起始位置，第五个句子为结束位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#44)]
     [!code-vb[Trin_VstcoreWordAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#44)]  
  
## 文档级自定义项示例  
  
#### 在文档级自定义项中重置现有范围  
  
1.  下面的示例显示文档级自定项的完整示例。 若要使用此代码，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#42)]  
  
## VSTO 外接程序示例  
  
#### 在 VSTO 外接程序中重置现有范围  
  
1.  下面的示例显示 VSTO 外接程序的完整示例。 若要使用此代码，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#42)]  
  
## 请参阅  
 [如何：以编程方式在文档中扩展范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以编程方式检索范围中的开始字符和结束字符](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何：以编程方式折叠文档中的范围或选定内容](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  