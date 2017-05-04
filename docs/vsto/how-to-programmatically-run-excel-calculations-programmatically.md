---
title: "如何：以编程方式运行 Excel 计算 | Microsoft Docs"
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
  - "计算, 在 Excel 中运行"
  - "Excel [Visual Studio 中的 Office 开发], 以编程方式进行计算"
  - "范围, 进行计算"
  - "工作簿, 进行计算"
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：以编程方式运行 Excel 计算
  使用类似的过程可以在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件或本机 Excel 区域对象中运行计算。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 在 NamedRange 控件中运行计算  
 下面的示例在单元格 A1 处创建一个 <xref:Microsoft.Office.Tools.Excel.NamedRange>，然后计算该单元格。  此代码必须放置在一个表类中，而不是放在 `ThisWorkbook` 类中。  
  
#### 在 NamedRange 控件中运行计算  
  
1.  创建命名范围。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#75)]  
  
2.  调用指定范围的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#76)]  
  
## 在本机 Excel 区域中运行计算  
  
#### 在本机 Excel 区域中运行计算  
  
1.  创建命名范围。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#30)]  
  
2.  调用指定范围的 <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#31)]  
  
## 请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  