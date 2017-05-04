---
title: "如何：以编程方式检索范围中的开始字符和结束字符 | Microsoft Docs"
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
  - "范围，检索开始和结束字符"
  - "结束字符"
  - "开始字符"
  - "文档 [Visual Studio 中的 Office 开发]，检索范围"
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 如何：以编程方式检索范围中的开始字符和结束字符
  此示例演示如何检索范围开始和结束位置的字符位置。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 检索文档级自定义项中范围的开始和结束字符  
  
1.  获取 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 的值和 <xref:Microsoft.Office.Interop.Word.Range> 对象的 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 属性。 下面的代码示例获取了文档中第二个语句的开始和结束位置。 若要使用此代码示例，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#25)]  
  
### 使用 VSTO 外接程序检索范围的开始和结束字符  
  
1.  获取 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 的值和 <xref:Microsoft.Office.Interop.Word.Range> 对象的 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 属性。 下面的代码示例获取了活动文档中第二个语句的开始和结束位置。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
## 请参阅  
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以编程方式在文档中扩展范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以编程方式重置 Word 文档中的范围](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以编程方式折叠文档中的范围或选定内容](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以编程方式在创建范围时排除段落标记](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [如何：以编程方式统计文档中的字符数](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  