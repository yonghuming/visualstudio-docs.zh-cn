---
title: "如何：以编程方式关闭文档 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发]，关闭"
  - "Word [Visual Studio 中的 Office 开发]，关闭文档"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# 如何：以编程方式关闭文档
  可以关闭活动文档，也可以指定关闭某个文档。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 关闭活动文档  
 关闭活动文档有两个过程：一个用于文档级自定义项；另一个用于 VSTO 外接程序。  
  
#### 关闭文档级自定义项中的活动文档  
  
1.  调用项目中 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.Document.Close%2A> 方法，以关闭与自定义关联的文档。 若要使用以下代码示例，请从 `ThisDocument` 类中运行它。  
  
    > [!NOTE]  
    >  此示例将 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值传递给要关闭的 *SaveChanges* 参数，而无需保存更改或提示用户。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### 关闭 VSTO 外接程序中的活动文档  
  
1.  调用 <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> 属性的 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 方法，以关闭活动文档。 若要使用下面的代码示例，请从项目的 `ThisAddIn` 类中运行它。  
  
    > [!NOTE]  
    >  此示例将 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值传递给要关闭的 *SaveChanges* 参数，而无需保存更改或提示用户。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 关闭按名称指定的文档  
 对于 VSTO 外接程序和文档级自定义项来说，按名称指定的文档的关闭方式是相同的。  
  
#### 关闭按名称指定的文档  
  
1.  将文档名称指定为 <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> 集合的参数，然后调用 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 方法。 以下代码示例假设在 Word 中打开了名为 **NewDocument** 的文档。  
  
    > [!NOTE]  
    >  此示例将 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值传递给要关闭的 *SaveChanges* 参数，而无需保存更改或提示用户。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## 请参阅  
 [如何：以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何：以编程方式保存文档](../vsto/how-to-programmatically-save-documents.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  