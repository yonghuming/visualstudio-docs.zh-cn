---
title: "如何：以编程方式在工作表单元格中显示字符串 | Microsoft Docs"
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
  - "文本 [Visual Studio 中的 Office 开发], 添加到工作表"
  - "工作表, 在单元格中显示文本"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 如何：以编程方式在工作表单元格中显示字符串
  此示例演示如何以编程方式在单元格中显示文本。  若要在单元格中显示文本，请使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件或本机 Excel 范围对象。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用 NamedRange 控件  
 此示例使用一个名为 `message` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  必须在设计时将此控件添加到文档级自定义项中。  必须将下面的代码放置到某个表类中，而不是放置到 `ThisWorkbook` 类中。  
  
#### 在 NamedRange 控件中显示文本  
  
1.  将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的值设置为 **Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## 使用本机 Excel 范围  
 下面的代码以编程方式创建一个新范围，然后为其赋值。  
  
#### 在 Excel 范围中显示文本  
  
1.  在 `Sheet1` 的单元格**“A1”**中检索范围并将值设置为 **Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## 请参阅  
 [演练：使用 Windows 窗体收集数据](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Office 解决方案的疑难解答](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  