---
title: "如何：以编程方式在文档中检查拼写"
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
  - "文档 [Visual Studio 中的 Office 开发], 检查拼写"
  - "拼写检查器, 文档"
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：以编程方式在文档中检查拼写
  若要在文档中检查拼写，请使用 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 方法。  此方法返回一个布尔值，该值指示所提供的参数是否拼写正确。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 检查拼写并在消息框中显示结果  
  
1.  调用 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 方法，并将它传给文本范围，以检查拼写错误。  若要使用此代码示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#113](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#113)]
     [!code-vb[Trin_VstcoreWordAutomation#113](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#113)]  
  
## 请参阅  
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  