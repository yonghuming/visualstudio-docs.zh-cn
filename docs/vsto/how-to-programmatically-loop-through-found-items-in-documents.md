---
title: "如何：以编程方式遍历在文档中找到的项"
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
  - "循环，通过在文档中找到的项"
  - "文档 [Visual Studio 中的 Office 开发]，搜索"
  - "文本 [Visual Studio 中的 Office 开发]，在文档中搜索"
ms.assetid: 68dc41b1-eb96-4697-ac93-1a88c862ebad
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以编程方式遍历在文档中找到的项
  <xref:Microsoft.Office.Interop.Word.Find> 类具有 <xref:Microsoft.Office.Interop.Word.Find.Found%2A> 属性，它在找到被搜索项时将返回 **true**。 你可以使用 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法循环访问在 <xref:Microsoft.Office.Interop.Word.Range> 中找到的所有实例。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 循环访问找到的项  
  
1.  声明 <xref:Microsoft.Office.Interop.Word.Range> 对象。  
  
     下面的代码示例可用于文档级自定义项。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#79)]  
  
     以下代码示例可用于 VSTO 外接程序。 本示例使用活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#79)]  
  
2.  循环使用 <xref:Microsoft.Office.Interop.Word.Find.Found%2A> 属性来搜索文档中字符串的所有匹配项，每次找到该字符串时整数变量递增 1。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#80)]
     [!code-vb[Trin_VstcoreWordAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#80)]  
  
3.  在消息框中显示找到字符串的次数。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#81](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#81)]
     [!code-vb[Trin_VstcoreWordAutomation#81](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#81)]  
  
 以下示例显示了完整方法。  
  
## 文档级自定义项示例  
  
#### 循环访问文档级自定义项中的项  
  
1.  下面的示例显示文档级自定项的完整代码。 若要使用此代码，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#78)]  
  
## VSTO 外接程序示例  
  
#### 循环访问 VSTO 外接程序中的项  
  
1.  下面的示例显示 VSTO 外接程序的完整代码。 若要使用此代码，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#78)]  
  
## 请参阅  
 [如何：以编程方式在文档中搜索和替换文本](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [如何：以编程方式在 Word 中设置搜索选项](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以编程方式在搜索后还原选定内容](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  