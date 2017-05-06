---
title: "如何：以编程方式在工作表之间复制数据和格式设置"
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
  - "复制数据, Visual Studio 中的 Office 开发"
  - "数据 [Visual Studio 中的 Office 开发], 在工作表之间复制"
  - "格式设置 [Visual Studio 中的 Office 开发]"
  - "工作表, 复制数据"
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 如何：以编程方式在工作表之间复制数据和格式设置
  通过使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> 方法，可以将工作簿中一个表上某个范围内的数据复制到此工作簿中的所有其他表上。  指定一个范围，并指定是要复制数据、格式设置还是复制两者。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#44)]  
  
## 编译代码  
 此示例要求工作表中有一个名为 `rangeData` 的范围。  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式向工作簿添加新工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [如何：以编程方式在包含选定单元格的工作表行中更改格式设置](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  