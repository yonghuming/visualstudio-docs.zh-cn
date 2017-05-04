---
title: "如何：以编程方式打开现有文档 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发], 打开"
  - "Word [Visual Studio 中的 Office 开发], 打开文档"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以编程方式打开现有文档
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 方法打开完全限定路径和文件名所指定的现有 Microsoft Office Word 文档。  此方法返回 <xref:Microsoft.Office.Interop.Word.Document>，它表示打开的文档。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 打开文档  
  
-   调用 <xref:Microsoft.Office.Interop.Word.Documents> 集合的 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 方法，并提供文档的路径。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### 以只读方式打开文档  
  
-   调用 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 方法，提供文档的路径，并在方法调用中将 *ReadOnly* 参数设置为 **True**。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## 编译代码  
 此代码示例要求满足以下条件：  
  
-   驱动器 C 上名为 Test 的目录中必须存在一个名为 NewDocument.doc 的文档。  
  
## 请参阅  
 [如何：以编程方式新建文档](../vsto/how-to-programmatically-create-new-documents.md)   
 [如何：以编程方式关闭文档](../vsto/how-to-programmatically-close-documents.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  