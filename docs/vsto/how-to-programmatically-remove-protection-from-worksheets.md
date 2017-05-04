---
title: "如何：以编程方式取消工作表保护 | Microsoft Docs"
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
  - "工作表，取消保护"
  - "文档 [Visual Studio 中的 Office 开发]，文档保护"
  - "文档保护，从工作表移除"
  - "移除保护方法"
ms.assetid: 034688d2-eda7-4b4a-bcc2-d0999ff879a4
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以编程方式取消工作表保护
  可以编程方式取消 Microsoft Office Excel 工作表保护。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 以下示例使用变量 `getPasswordFromUser`，该变量包含获取自用户的密码。  
  
### 若要在文档级自定义中取消工作表的保护  
  
1.  调用工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> 方法并传入密码（如果需要）。 此示例假定你正在使用名为 `Sheet1` 的工作表。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#28)]  
  
### 在 VSTO 外接程序中取消工作表保护  
  
1.  调用活动工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> 方法并传入密码（如果需要）。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式保护工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [如何：以编程方式保护工作簿](../vsto/how-to-programmatically-protect-workbooks.md)   
 [如何：以编程方式隐藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)  
  
  