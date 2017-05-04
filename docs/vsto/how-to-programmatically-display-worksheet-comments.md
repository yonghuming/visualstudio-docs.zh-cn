---
title: "如何：以编程方式显示工作表注释 | Microsoft Docs"
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
  - "工作表，注释"
  - "注释，工作表"
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：以编程方式显示工作表注释
  可以在 Microsoft Office Excel 工作表中以编程方式显示和隐藏注释。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在文档级自定义项的工作表中显示所有注释  
  
1.  若想显示注释，请将 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 属性设置为 **true**；否则为 **false**。 必须将此代码置于表类中，而不是在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#31)]  
  
### 在应用程序级 VSTO 外接程序的工作表中显示所有注释  
  
1.  若想显示注释，请将 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 属性设置为 **true**；否则为 **false**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式添加和删除工作表注释](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
  