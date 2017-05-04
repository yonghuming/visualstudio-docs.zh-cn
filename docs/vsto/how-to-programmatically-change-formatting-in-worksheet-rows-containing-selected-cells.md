---
title: "如何：以编程方式在包含选定单元格的工作表行中更改格式设置 | Microsoft Docs"
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
  - "格式设置 [Visual Studio 中的 Office 开发]"
  - "行 [Visual Studio 中的 Office 开发]"
  - "工作表, 更改格式设置"
ms.assetid: c55cd488-98d1-46c6-9715-0e9212d178de
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 如何：以编程方式在包含选定单元格的工作表行中更改格式设置
  可以更改包含选定单元格的整行的字体，使其中的文本变成粗体。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 使当前行变成粗体、使前面的粗体行恢复正常  
  
1.  声明一个静态变量以跟踪前面选定的行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#37)]  
  
2.  使用 <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> 属性检索对当前单元格的引用。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#38)]  
  
3.  使用活动单元格的 <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> 属性将当前行设为粗体样式。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#39)]  
  
4.  请确保 `previousRow` 的当前值不为 0。  0（零）指示这是第一次执行此代码。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#40)]  
  
5.  确保当前行不同于上一行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#41)]  
  
6.  检索对表示前面选定的行的范围的引用，并将该行设置为非粗体。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#42)]  
  
7.  存储当前行，以便使它在下次传递时成为前一行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#43)]  
  
 下面的示例演示完整的方法。  
  
## 示例  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#36)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式将样式应用于工作簿中的所选区域](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以编程方式在工作表之间复制数据和格式设置](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  