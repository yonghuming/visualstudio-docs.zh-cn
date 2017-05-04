---
title: "如何：在受密码保护的文档中缓存数据 | Microsoft Docs"
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
  - "数据 [Visual Studio 中的 Office 开发], 缓存"
  - "数据缓存 [Visual Studio 中的 Office 开发], 受保护的文档"
  - "数据集 [Visual Studio 中的 Office 开发], 缓存"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：在受密码保护的文档中缓存数据
  如果向受密码保护的文档或工作簿中的数据缓存添加数据，则不自动保存对缓存数据所做的更改。  您可以通过在项目中重写两个相应的方法来保存对缓存数据所做的更改。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 在 Word 文档中执行缓存  
  
#### 在受密码保护的 Word 文档中缓存数据  
  
1.  在 `ThisDocument` 类中，标记要缓存的公共字段或属性。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。  
  
2.  在 `ThisDocument` 类中重写 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 方法，取消对文档的保护。  
  
     保存文档时，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会调用此方法，以便为您提供取消文档保护的机会。  这使您可以保存对缓存数据所做的更改。  
  
3.  重写 `ThisDocument` 类中的 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 方法，并对文档重新应用保护。  
  
     保存文档后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会调用此方法，以便为您提供对文档重新应用保护的机会。  
  
### 示例  
 下面的代码示例演示如何在受密码保护的 Word 文档中缓存数据。  代码在 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 方法中取消保护之前，将保存当前的 <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> 值，以便可以在 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 方法中重新应用相同类型的保护。  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### 编译代码  
 将此代码添加到项目的 `ThisDocument` 类中。  此代码假定密码存储在一个名为 `securelyStoredPassword` 的字段中。  
  
## 在 Excel 工作簿中执行缓存  
 在 Excel 项目中，仅当通过 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 方法使用密码保护整个工作簿后，才需要执行此过程。  如果通过 <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> 方法使用密码来保护某个特定的工作簿，则不需要执行此过程。  
  
#### 在受密码保护的 Excel 工作簿中缓存数据  
  
1.  在 `ThisWorkbook` 类或某个 `Sheet`*n* 类中，标记要缓存的公共字段或属性。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。  
  
2.  在 `ThisWorkbook` 类中重写 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 方法，取消对工作簿的保护。  
  
     保存工作簿时，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会调用此方法，以便为您提供取消工作簿保护的机会。  这使您可以保存对缓存数据所做的更改。  
  
3.  重写 `ThisWorkbook` 类中的 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 方法，并对文档重新应用保护。  
  
     保存工作簿后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会调用此方法，以便为您提供对工作簿重新应用保护的机会。  
  
### 示例  
 下面的代码示例演示如何在受密码保护的 Excel 工作簿中缓存数据。  代码在 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 方法中取消保护之前，将保存当前的 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> 和 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> 值，以便可以在 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 方法中重新应用相同类型的保护。  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### 编译代码  
 将此代码添加到项目的 `ThisWorkbook` 类中。  此代码假定密码存储在一个名为 `securelyStoredPassword` 的字段中。  
  
## 请参阅  
 [缓存数据](../vsto/caching-data.md)   
 [如何：缓存数据以便脱机使用或在服务器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：以编程方式在 Office 文档中缓存数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  