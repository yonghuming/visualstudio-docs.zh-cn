---
title: "如何：以编程方式在打印预览中显示文档"
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
  - "Word [Visual Studio 中的 Office 开发]，在打印预览中显示文档"
  - "文档 [Visual Studio 中的 Office 开发]，在打印预览中显示"
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：以编程方式在打印预览中显示文档
  如果你的解决方案生成了报告，你可能需要以打印预览模式向用户显示报告。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 适用于文档级自定义项的过程  
  
#### 通过调用 PrintPreview 方法在打印预览中显示文档  
  
1.  调用 <xref:Microsoft.Office.Tools.Word.Document> 类的 <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> 方法。 若要使用此代码示例，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomation#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#13)]  
  
#### 通过设置 PrintPreview 属性在打印预览中显示文档  
  
1.  将 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Application> 属性设置为 **true**。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## 适用于 VSTO 外接程序的过程  
  
#### 通过调用 PrintPreview 方法在打印预览中显示文档  
  
1.  调用要预览的 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> 方法。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
#### 通过设置 PrintPreview 属性在打印预览中显示文档  
  
1.  将 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Application> 属性设置为 **true**。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## 请参阅  
 [如何：以编程方式打印文档](../vsto/how-to-programmatically-print-documents.md)   
 [如何：以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何：以编程方式新建文档](../vsto/how-to-programmatically-create-new-documents.md)  
  
  