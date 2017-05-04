---
title: "如何：以编程方式选择工作表 | Microsoft Docs"
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
  - "Excel 项目, 选择工作表"
  - "工作表, 选择"
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以编程方式选择工作表
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> 方法选择指定的对象，从而将用户的选择移到新对象上。  如果想要将焦点移到对象上，而不更改用户的选择，请使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> 方法。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 如果想要在 VSTO 外接程序中选择现有工作表，或者在文档级自定义项中已在运行时创建了工作表，则必须使用 Excel 工作簿的 Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 集合来访问它；否则可以直接访问 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主机项。  
  
## 使用工作表主机项  
 在文档级自定义项中，将下面的代码添加到 **Sheet1.vb** 或 **Sheet1.cs** 中。  
  
#### 使用主机项选择工作簿中的第一个工作表  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> 的 `Sheet1` 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#19)]  
  
## 使用 Excel 工作簿的表集合  
 使用 Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 集合访问工作表。  
  
#### 使用 Excel 工作簿的 Sheets 集合选择工作簿中的第一个工作表  
  
1.  调用 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> 方法来选择活动工作薄中的第一个工作表。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#20)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式打印工作表](../vsto/how-to-programmatically-print-worksheets.md)   
 [如何：以编程方式从工作簿中删除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以编程方式隐藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [如何：以编程方式保护工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [工作表宿主项](../vsto/worksheet-host-item.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
  