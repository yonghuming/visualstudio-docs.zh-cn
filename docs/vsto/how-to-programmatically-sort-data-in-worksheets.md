---
title: "如何：以编程方式对工作表中的数据进行排序 | Microsoft Docs"
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
  - "数据 [Visual Studio 中的 Office 开发], 在工作表中排序"
  - "数据排序, 工作表"
  - "对数据进行排序, 在工作表中"
  - "工作表, 对数据进行排序"
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 如何：以编程方式对工作表中的数据进行排序
  在运行时，可以对工作表区域和列表中所包含数据进行排序。  以下代码先按第一列中的数据对名为 `Fruits` 的多列区域进行排序，然后按第二列中的数据进行相同操作。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 对文档级自定义项中的数据进行排序  
  
#### 若要对 NamedRange 控件中的数据进行排序  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> 方法。  以下示例需要工作表上一个名为 `Fruits` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  必须将此代码置于表类中，而不是在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#78)]  
  
 将以下代码置于 Sheet1.vb 或 Sheet1.cs 中，以对 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件中的数据进行排序。  该代码假定你在名为 `Sheet1` 的工作表中，具有名为 `fruitList` 的 <xref:Microsoft.Office.Tools.Excel.ListObject>控件。  
  
#### 对 ListObject 控件中的数据进行排序  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject> 主机控件的 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 属性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#79)]  
  
## 对 VSTO 外接程序中的数据进行排序  
  
#### 若要对本机范围内的数据进行排序  
  
1.  调用本机 Excel <xref:Microsoft.Office.Interop.Excel.Range> 控件的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  以下示例需要工作表上一个名为 `Fruits` 的本机 Excel 控件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
#### 对 ListObject 控件中的数据进行排序  
  
1.  调用本机 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控件的 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>属性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  以下示例假定你在活动工作表中有名为 `fruitList` 的本机 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式自动用递增变化的数据填充范围](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何：以编程方式使用代码引用工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何：以编程方式将样式应用于工作簿中的所选区域](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [ListObject 控件](../vsto/listobject-control.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  