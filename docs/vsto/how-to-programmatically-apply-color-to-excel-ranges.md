---
title: "如何：以编程方式将颜色应用于 Excel 范围"
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
  - "颜色, Excel 范围"
  - "格式设置 [Visual Studio 中的 Office 开发]"
  - "范围, 应用颜色"
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：以编程方式将颜色应用于 Excel 范围
  若要将颜色应用于一系列单元格内的文本，请使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件或本机 Excel 范围对象。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用 NamedRange 控件  
 此示例针对的是文档级自定义项。  
  
#### 对 NamedRange 控件应用颜色  
  
1.  在单元格“A1”中创建一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#65)]  
  
2.  设置 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件中文本的颜色。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#66)]  
  
## 使用本机 Excel 范围  
  
#### 将颜色应用于本机 Excel 范围对象  
  
1.  在单元格 A1 处创建一个范围，然后设置文本的颜色。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#67)]  
  
## 请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [如何：以编程方式将样式应用于工作簿中的所选区域](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以编程方式使用代码引用工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  