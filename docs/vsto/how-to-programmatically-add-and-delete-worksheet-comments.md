---
title: "如何：以编程方式添加和删除工作表注释 | Microsoft Docs"
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
  - "区域，注释"
  - "工作表，注释"
  - "注释，工作表"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 如何：以编程方式添加和删除工作表注释
  可以以编程方式在 Microsoft Office Excel 工作表中添加和删除注释。 可以仅向单个单元格而非多单元格区域添加注释。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 在文档级项目中添加和删除注释  
 下面的示例假定名为 `Sheet1` 的工作表上存在名为 `dateComment` 的单单元格 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
#### 向命名区域添加新的注释  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的 <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> 方法并提供注释文本。 必须将此代码置于 `Sheet1` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### 删除命名区域中的注释  
  
1.  验证区域中是否存在注释并将其删除。 必须将此代码置于 `Sheet1` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## 在 VSTO 外接程序项目中添加和删除注释  
 下面的示例假定活动的工作表上存在名为 `dateComment` 的单单元格 <xref:Microsoft.Office.Interop.Excel.Range>。  
  
#### 向 Excel 区域添加新的注释  
  
1.  调用 <xref:Microsoft.Office.Interop.Excel.Range> 的 <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> 方法并提供注释文本。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### 删除 Excel 区域中的注释  
  
1.  验证区域中是否存在注释并将其删除。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式显示工作表注释](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)  
  
  