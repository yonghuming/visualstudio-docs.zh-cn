---
title: "如何：以编程方式打印文档 | Microsoft Docs"
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
  - "Word [Visual Studio 中的 Office 开发]，打印文档"
  - "文档 [Visual Studio 中的 Office 开发]，打印"
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 如何：以编程方式打印文档
  你可以将整个 Microsoft Office Word 文档或文档的一部分打印到默认打印机。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 打印属于文档级自定义项的文档  
  
#### 若要打印整个文档  
  
1.  调用项目中 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 方法以打印整个文档。 若要使用此示例，请在 `ThisDocument` 类中运行代码。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#11)]  
  
#### 若要打印文档的当前页面  
  
1.  调用项目中 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 方法并指定打印一份当前页面。 若要使用此示例，请在 `ThisDocument` 类中运行代码。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomation#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#12)]  
  
## 使用 VSTO 外接程序打印文档  
  
#### 若要打印整个文档  
  
1.  调用要打印的 <xref:Microsoft.Office.Interop.Word.Document> 对象的 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 方法。 下面的代码示例将打印活动文档。 若要使用此示例，请从项目的 `ThisAddIn` 类中运行代码。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
#### 若要打印文档的当前页面  
  
1.  调用要打印的 <xref:Microsoft.Office.Interop.Word.Document> 对象的 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 方法，并指定打印一份当前页面。 下面的代码示例将打印活动文档。 若要使用此示例，请从项目的 `ThisAddIn` 类中运行代码。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## 请参阅  
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  