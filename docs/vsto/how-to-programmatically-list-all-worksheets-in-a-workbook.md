---
title: "如何：以编程方式列出工作簿中的所有工作表 | Microsoft Docs"
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
  - "工作簿, 列出工作表"
  - "工作表, 列出"
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以编程方式列出工作簿中的所有工作表
  <xref:Microsoft.Office.Interop.Excel.Workbook> 类提供一个 <xref:Microsoft.Office.Interop.Excel.Worksheets> 对象。  此对象包含工作簿中所有 <xref:Microsoft.Office.Interop.Excel.Worksheet> 对象的集合。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在文档级自定义项中列出工作簿中所有现有的工作表  
  
1.  循环访问 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合，将每个表的名称发送到通过 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件偏移的单元格。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#21)]  
  
### 若要列出 VSTO 外接程序中的工作簿中的所有现有工作表  
  
1.  循环访问 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合，将每个表的名称发送到与 <xref:Microsoft.Office.Interop.Excel.Range> 对象偏移一定量的单元格。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式向工作簿添加新工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [如何：以编程方式在工作簿中移动工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)  
  
  