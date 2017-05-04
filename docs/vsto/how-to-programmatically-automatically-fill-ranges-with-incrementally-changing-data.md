---
title: "如何：以编程方式自动用递增变化的数据填充范围 | Microsoft Docs"
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
  - "Autofill 方法 [Excel]"
  - "自动添加范围"
  - "范围, 自动填充"
  - "工作簿, 填充范围"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 如何：以编程方式自动用递增变化的数据填充范围
  通过 <xref:Microsoft.Office.Interop.Excel.Range> 对象的 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法，可以自动向工作表中的范围填充值。  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法通常用于向一个范围中增量存储递增或递减的值。  可以通过提供 <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> 枚举中的可选常数来指定行为。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 使用 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 时必须指定两个范围：  
  
-   调用 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法的范围，此范围指定填充的起始点并且包含一个初始值。  
  
-   要填充的范围，作为参数传递给 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法。  目标范围必须包括包含初始值的范围。  
  
    > [!NOTE]  
    >  不能传递 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件替换 <xref:Microsoft.Office.Interop.Excel.Range>。  有关更多信息，请参见[宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## 示例  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## 编译代码  
 要填充的范围的第一个单元格必须包含初始值。  
  
 此示例要求填充三个区域：  
  
-   列 B 将包含 5 个工作日。  请在 B1 单元格中键入**“Monday”**作为初始值。  
  
-   列 C 将包含 5 个月份。  请在 C1 单元格中键入**“January”**作为初始值。  
  
-   列 D 将包含一系列数字，每行依次递增 2。  请在 D1 单元格中键入**“4”**，在 D2 单元格中键入**“6”**，并将这两个值作为初始值。  
  
## 请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [如何：以编程方式使用代码引用工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何：以编程方式将样式应用于工作簿中的所选区域](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以编程方式运行 Excel 计算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  