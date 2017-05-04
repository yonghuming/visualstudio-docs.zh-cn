---
title: "如何：以编程方式在搜索后还原选定内容 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发], 还原选择"
  - "搜索, 此后还原选择"
  - "选定内容, 搜索后还原"
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 如何：以编程方式在搜索后还原选定内容
  如果查找并替换文档中的文本，在搜索结束后可能需要还原用户原来的选择。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 示例过程中的代码使用了两个 <xref:Microsoft.Office.Interop.Word.Range> 对象。  一个存储当前的 <xref:Microsoft.Office.Interop.Word.Selection>，另一个将整个文档设置为搜索范围。  
  
### 搜索后恢复用户原来的选择  
  
1.  为文档和当前选择创建 <xref:Microsoft.Office.Interop.Word.Range> 对象。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#83)]
     [!code-vb[Trin_VstcoreWordAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#83)]  
  
2.  执行搜索和替换操作。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#84](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#84)]
     [!code-vb[Trin_VstcoreWordAutomation#84](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#84)]  
  
3.  选择要还原用户原来的选择的开始范围。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#85](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#85)]
     [!code-vb[Trin_VstcoreWordAutomation#85](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#85)]  
  
 下面的示例演示完整的方法。  
  
## 示例  
 [!code-csharp[Trin_VstcoreWordAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#82)]
 [!code-vb[Trin_VstcoreWordAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#82)]  
  
## 请参阅  
 [如何：以编程方式在文档中搜索和替换文本](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [如何：以编程方式在 Word 中设置搜索选项](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [如何：以编程方式遍历在文档中找到的项](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  