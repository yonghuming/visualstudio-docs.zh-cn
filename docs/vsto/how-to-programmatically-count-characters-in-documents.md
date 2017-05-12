---
title: "如何：以编程方式统计文档中的字符数"
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
  - "字符，在文档中计数"
  - "统计文档中的字符数"
  - "文档 [Visual Studio 中的 Office 开发]，统计字符数"
ms.assetid: ab64fe87-896a-4b56-bdf8-91c4326b540e
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 如何：以编程方式统计文档中的字符数
  文档中的第一个字符位于字符位置 0，它表示插入点。 末尾字符位置值与文档中的字符总数相同。 可以使用 <xref:Microsoft.Office.Interop.Word.Characters> 集合的 <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> 属性确定文档中的字符数。  
  
 文档中的所有字符都被计算在内，包括空格、段落标记及通常是隐藏的其他字符。 甚至一个新的空文档的计数结果都返回一个字符，因为它包含一个段落标记。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 显示文档级自定义项中的字符数  
  
1.  选择整个文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomation#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#98)]  
  
2.  在一个消息框中显示文档中的字符数。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomation#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#99)]  
  
### 显示 VSTO 外接程序中的字符数  
  
1.  选择整个文档。 下面的示例将选择活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#98)]  
  
2.  在一个消息框中显示文档中的字符数。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#99)]  
  
## 请参阅  
 [如何：以编程方式检索范围中的开始字符和结束字符](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  