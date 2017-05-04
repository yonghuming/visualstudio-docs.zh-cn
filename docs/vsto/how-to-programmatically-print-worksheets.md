---
title: "如何：以编程方式打印工作表 | Microsoft Docs"
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
  - "打印预览, 工作表"
  - "打印 [Visual Studio 中的 Office 开发], 工作表"
  - "工作表, 打印"
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以编程方式打印工作表
  可以打印工作簿中的任何工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 打印文档级自定义项中的工作表  
  
#### 打印工作表  
  
1.  先调用 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> 方法，请求两个副本，然后预览文档，再进行打印。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#22)]  
  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> 方法使你能够在**“打印预览”**窗口中显示指定的对象。  以下代码假定你已具有一个名为 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主机项。  
  
#### 在打印之前预览页面  
  
1.  调用工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#23)]  
  
## 打印 VSTO 外接程序中的工作表  
  
#### 打印工作表  
  
1.  先调用活动工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> 方法，请求两个副本，然后预览文档，再进行打印。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 方法使你能够在**“打印预览”**窗口中显示指定的对象。  
  
#### 在打印之前预览页面  
  
1.  调用活动工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式在工作表中检查拼写](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [工作表宿主项](../vsto/worksheet-host-item.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  