---
title: "如何：以编程方式列出最近使用的工作簿文件"
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
  - "Excel [Visual Studio 中的 Office 开发], 最近使用过的文件列表"
  - "近期文件列表, Excel"
  - "RecentFiles 属性"
  - "工作簿, 列出最近使用过的"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：以编程方式列出最近使用的工作簿文件
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> 属性返回一个集合，该集合包含 Microsoft Office Excel 最近使用的文件列表中出现的所有文件名。  列表长度因用户选择要保留的文件数而异。  您可以在某一范围内显示结果。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在区域对象中列出最近使用的工作簿  
  
1.  遍历最近使用的文件的列表，并将名称显示在相对于 <xref:Microsoft.Office.Interop.Excel.Range> 对象的单元格中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## 请参阅  
 [使用工作簿](../vsto/working-with-workbooks.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  