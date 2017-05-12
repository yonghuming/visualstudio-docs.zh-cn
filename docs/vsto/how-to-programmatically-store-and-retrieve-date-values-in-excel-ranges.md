---
title: "如何：以编程方式在 Excel 范围内存储和检索日期值"
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
  - "日期值"
  - "日期值, 在 Excel 范围中存储"
  - "日期, 从 Excel 范围中检索"
  - "日期, 在 Excel 范围中存储"
  - "Excel [Visual Studio 中的 Office 开发], 从范围中检索日期值"
  - "Excel [Visual Studio 中的 Office 开发], 在范围中存储日期值"
  - "范围, 检索日期值"
  - "范围, 存储日期值"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：以编程方式在 Excel 范围内存储和检索日期值
  可以在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件或本机 Excel 范围对象中存储和检索值。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 如果使用 Visual Studio 中的 Office 开发工具在某个范围内存储了 1\/1\/1900 及以后的日期值，此值将以 OLE 自动化 \(OA\) 格式存储。  必须使用 <xref:System.DateTime.FromOADate%2A> 方法检索 OLE 自动化 \(OA\) 日期的值。  如果日期早于 1\/1\/1900，它将以字符串形式存储。  
  
> [!NOTE]  
>  Excel 日期与 OLE 自动化日期的不同之处在于 1900 年的头两个月。  如果选中了**“1904 日期系统”**选项，也会有不同之处。  下面的代码示例不考虑这些差异。  
  
## 使用 NamedRange 控件  
  
-   此示例针对的是文档级自定义项。  必须将下面的代码放置到某个表类中，而不是放置到 `ThisWorkbook` 类中。  
  
#### 在命名范围内存储日期值  
  
1.  在单元格**“A1”**中创建一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  将今天的日期设置为 `NamedRange1` 的值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### 从命名范围中检索日期值  
  
1.  从 `NamedRange1` 中检索日期值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## 使用本机 Excel 范围  
  
#### 在本机 Excel 范围对象中存储日期值  
  
1.  创建一个表示单元格**“A1”**的 <xref:Microsoft.Office.Interop.Excel.Range>。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  将今天的日期设置为 `rng` 的值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### 从本机 Excel 范围对象中检索日期值  
  
1.  从 `rng` 中检索日期值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## 请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [Excel 对象模型概述](../vsto/excel-object-model-overview.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [如何：以编程方式使用代码引用工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何：向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  