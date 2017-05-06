---
title: "如何：以编程方式保护工作簿"
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
  - "文档保护, 向工作簿添加"
  - "文档保护, 从工作簿移除"
  - "文档 [Visual Studio 中的 Office 开发], 文档保护"
  - "工作簿, 密码"
  - "工作簿, 保护"
  - "工作簿, 取消保护"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：以编程方式保护工作簿
  可以保护 Microsoft Office Excel 工作簿，使用户无法添加或删除工作表，并且还可以通过编程方式取消对工作簿的保护。  您可以选择指定一个密码，指示是否希望保护该结构（使用户无法移动表）以及指示是否希望保护工作簿的窗口。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 保护工作簿并不会阻止用户编辑单元格。  若要保护数据，您必须保护工作表。  有关更多信息，请参见[如何：以编程方式保护工作表](../vsto/how-to-programmatically-protect-worksheets.md)。  
  
 下面的代码示例使用变量来存放从用户那里获取的密码。  
  
## 保护属于文档级自定义项一部分的工作簿  
  
#### 保护工作簿  
  
1.  调用工作簿的 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 方法并包含一个密码。  若要使用下面的代码示例，请在 `ThisWorkbook` 类中运行此示例，而不要在工作表类中运行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### 取消工作簿保护  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> 方法，如果需要，请传递一个密码。  若要使用下面的代码示例，请在 `ThisWorkbook` 类中运行此示例，而不要在工作表类中运行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## 使用应用程序级外接程序保护工作簿  
  
#### 保护工作簿  
  
1.  调用工作簿的 <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> 方法并包含一个密码。  此代码示例使用活动工作簿。  若要使用此示例，请从项目内的 `ThisAddIn` 类中运行代码。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### 取消工作簿保护  
  
1.  调用活动工作簿的 <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> 方法并根据需要传入密码。  若要使用此示例，请从项目内的 `ThisAddIn` 类中运行代码。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## 请参阅  
 [使用工作簿](../vsto/working-with-workbooks.md)   
 [如何：以编程方式保护工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [如何：以编程方式隐藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  