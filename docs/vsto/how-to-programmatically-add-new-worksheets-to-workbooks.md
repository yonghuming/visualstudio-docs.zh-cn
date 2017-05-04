---
title: "如何：以编程方式向工作簿添加新工作表 | Microsoft Docs"
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
  - "工作簿，添加工作表"
  - "工作簿，创建工作表"
  - "工作表，创建"
  - "工作表，向工作簿添加"
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# 如何：以编程方式向工作簿添加新工作表
  可以通过编程方式创建一个工作表，然后将它添加到工作簿中工作表的集合。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 将新工作表添加到文档级自定义项中的工作簿  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#15)]  
  
     新工作表是一个本机 <xref:Microsoft.Office.Interop.Excel.Worksheet> 对象，不是主机项。 如果想要添加 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主机项，则应在设计时添加工作表。  
  
### 将新工作表添加到 VSTO 外接程序中的工作簿  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
     新工作表是一个本机 <xref:Microsoft.Office.Interop.Excel.Worksheet> 对象，不是主机项。 你还可以从本机 <xref:Microsoft.Office.Interop.Excel.Worksheet> 对象生成 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主机项。 有关详细信息，请参阅[在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [如何：以编程方式从工作簿中删除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以编程方式选择工作表](../vsto/how-to-programmatically-select-worksheets.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  