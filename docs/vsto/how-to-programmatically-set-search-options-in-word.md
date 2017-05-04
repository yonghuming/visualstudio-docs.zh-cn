---
title: "如何：以编程方式在 Word 中设置搜索选项 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发], 搜索选项"
  - "搜索, Word 选项"
  - "设置, Word 搜索选项"
  - "Word, 搜索选项"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以编程方式在 Word 中设置搜索选项
  有两种方法可用于为 Microsoft Office Word 文档中的选定内容设置搜索选项：  
  
-   设置 <xref:Microsoft.Office.Interop.Word.Find> 对象的各个属性。  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Find> 对象的 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法的参数。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 使用 Find 对象的属性  
 以下代码设置 <xref:Microsoft.Office.Interop.Word.Find> 对象的属性，以便在当前的选定内容中搜索文本。  注意，向前搜索、换行及要搜索的文本等搜索条件都是 <xref:Microsoft.Office.Interop.Word.Find> 对象的属性。  
  
 编写 C\# 代码时设置 <xref:Microsoft.Office.Interop.Word.Find> 对象的每个属性没有用，因为您必须指定与 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法中的参数相同的属性。  因此，此示例仅包含 Visual Basic 代码。  
  
#### 使用 Find 对象设置搜索选项  
  
1.  设置 <xref:Microsoft.Office.Interop.Word.Find> 对象的属性，以便在选定内容中向前搜索文本**“find me”**。  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## 使用 Execute 方法参数  
 以下代码使用 <xref:Microsoft.Office.Interop.Word.Find> 对象的 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法在当前的选定内容中搜索文本。  注意，向前搜索、换行及要搜索的文本等搜索条件都作为 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法的参数进行传递。  
  
#### 使用 Execute 方法参数设置搜索选项  
  
1.  将搜索条件作为 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法的参数进行传递，以在选定内容中向前搜索文本**“find me”**。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## 请参阅  
 [如何：以编程方式在文档中搜索和替换文本](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [如何：以编程方式遍历在文档中找到的项](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [如何：以编程方式在搜索后还原选定内容](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  