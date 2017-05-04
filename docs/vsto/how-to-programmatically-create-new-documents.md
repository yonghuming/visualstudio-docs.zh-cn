---
title: "如何：以编程方式新建文档 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发], 创建"
  - "模板 [Visual Studio 中的 Office 开发], 自定义文档"
  - "Word [Visual Studio 中的 Office 开发], 创建文档"
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# 如何：以编程方式新建文档
  当以编程方式创建文档时，新文档是一个本机 <xref:Microsoft.Office.Interop.Word.Document> 对象。  此对象不具有 <xref:Microsoft.Office.Tools.Word.Document> 主机项的其他事件和数据绑定功能。  有关详细信息，请参阅[宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 开发文档级项目时，不能以编程方式将 <xref:Microsoft.Office.Tools.Word.Document> 主机项添加到你的项目。  在 VSTO 外接程序项目中，可在运行时将任意 <xref:Microsoft.Office.Interop.Word.Document> 对象转换为 <xref:Microsoft.Office.Tools.Word.Document> 主机项。  有关详细信息，请参阅[在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### 基于 Normal 模板创建新文档  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Documents> 集合的 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 方法来创建基于 Normal 模板的新文档。  若要使用此代码模板，请从项目中的 `ThisDocument` 或 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreWordAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#1)]  
  
## 使用自定义模板  
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 方法具有一个可选的 *Template* 参数，以基于模板（而非 Normal 末班）来创建新文档。  你必须提供模板的文件名称和完全限定路径。  
  
#### 基于自定义模板创建新文档  
  
-   调用 <xref:Microsoft.Office.Interop.Word.Documents> 集合的 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 方法，并指定模板的路径。  若要使用此代码模板，请从项目中的 `ThisDocument` 或 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreWordAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#2)]  
  
## 请参阅  
 [如何：以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  