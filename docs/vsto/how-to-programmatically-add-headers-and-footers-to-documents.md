---
title: "如何：以编程方式向文档中添加页眉和页脚 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发], 添加页脚"
  - "文档 [Visual Studio 中的 Office 开发], 添加页眉"
  - "页脚, 添加到文档"
  - "页眉, 添加到 Office 文档"
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：以编程方式向文档中添加页眉和页脚
  可以通过使用 <xref:Microsoft.Office.Interop.Word.Section> 的 <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> 属性和 <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> 属性将文本添加到文档中的页眉和页脚。  文档各部分均包含三个页眉和页脚：  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 对于文档级自定义项和 VSTO 外接程序，此过程有所不同。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 文档级自定义项  
 若要使用以下代码示例，请从项目中的 `ThisDocument` 类运行它们。  
  
#### 将文本添加到文档的页脚  
  
1.  以下代码示例设置要插入到文档各部分主页脚的文本字体，然后再将文本插入页脚。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomation#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#114)]  
  
#### 将文本添加到文档的页眉  
  
1.  以下代码示例将添加一个字段，以在文档各个页眉中显示页码，然后设置段落对齐方式，使文本对齐到页眉的右侧。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomation#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#116)]  
  
## VSTO 外接程序  
 若要使用以下代码示例，请从项目中的 `ThisAddIn` 类运行它们。  
  
#### 将文本添加到文档的页脚  
  
1.  以下代码示例设置要插入到文档各部分主页脚的文本字体，然后再将文本插入页脚。  此代码示例使用活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#114)]  
  
#### 将文本添加到文档的页眉  
  
1.  以下代码示例将添加一个字段，以在文档各个页眉中显示页码，然后设置段落对齐方式，使文本对齐到页眉的右侧。  此代码示例使用活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#116)]  
  
## 请参阅  
 [如何：以编程方式新建文档](../vsto/how-to-programmatically-create-new-documents.md)   
 [如何：以编程方式在文档中扩展范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以编程方式遍历在文档中找到的项](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
  
  