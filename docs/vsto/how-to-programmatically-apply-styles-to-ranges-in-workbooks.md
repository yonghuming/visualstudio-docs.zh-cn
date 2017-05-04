---
title: "如何：以编程方式将样式应用于工作簿中的所选区域 | Microsoft Docs"
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
  - "范围，样式"
  - "样式，工作簿范围"
  - "工作簿，样式"
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 如何：以编程方式将样式应用于工作簿中的所选区域
  可以将已命名的样式应用到工作簿中的区域。 Excel 提供了大量预定义样式。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 **“设置单元格格式”**对话框显示了可用于设置单元格格式的所有选项，且其中每个选项都可从你的代码获取。 若要在 Excel 中显示此对话框，请单击**“格式”**菜单上的**“单元格”**。  
  
### 将样式应用到文档级自定义项中的命名区域  
  
1.  创建一个新样式并设置其属性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#53)]  
  
2.  创建一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，向其分配文本，然后应用新样式。 必须将此代码置于表类中，而不是在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#54)]  
  
### 从文档级自定义项的命名区域中清除样式  
  
1.  将正文样式应用到该区域中。 必须将此代码置于表类中，而不是在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#55)]  
  
### 将样式应用到 VSTO 外接程序中的命名区域  
  
1.  创建一个新样式并设置其属性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#28)]  
  
2.  创建一个 <xref:Microsoft.Office.Interop.Excel.Range>，对其分配文本，然后应用新样式。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#29)]  
  
### 从 VSTO 外接程序的命名区域中清除样式  
  
1.  将正文样式应用到该区域中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#56)]  
  
## 请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  