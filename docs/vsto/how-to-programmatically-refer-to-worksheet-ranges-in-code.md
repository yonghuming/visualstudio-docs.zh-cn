---
title: "如何：以编程方式使用代码引用工作表范围"
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
  - "Excel [Visual Studio 中的 Office 开发], 引用工作表范围"
  - "范围, 引用"
  - "引用工作表范围"
  - "工作表, 引用范围"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：以编程方式使用代码引用工作表范围
  使用类似的过程可以引用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件或本机 Excel 区域对象的内容。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用 NamedRange 控件  
 下面的示例向工作表中添加一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，然后向该区域内的单元格中添加文本。  
  
#### 引用 NamedRange 控件  
  
1.  将字符串分配给 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 属性。  此代码必须放置在一个表类中，而不是放在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## 使用本机 Excel 范围  
 下面的示例向工作表中添加一个本机 Excel 区域，然后向该区域内的单元格中添加文本。  
  
#### 引用本机区域对象  
  
1.  向该区域的 <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 属性赋予一个字符串。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## 请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [如何：以编程方式在工作表中检查拼写](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [如何：以编程方式将样式应用于工作簿中的所选区域](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以编程方式自动用递增变化的数据填充范围](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何：以编程方式在工作表范围内搜索文本](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  