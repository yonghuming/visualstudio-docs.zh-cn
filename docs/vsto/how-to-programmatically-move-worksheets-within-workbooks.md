---
title: "如何：以编程方式在工作簿中移动工作表"
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
  - "工作表，移动"
  - "工作簿，移动工作表于"
ms.assetid: a010a633-412e-4299-9587-cacb035842c1
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以编程方式在工作簿中移动工作表
  可以通过编程方式更改工作簿中工作表相对于其他工作表的位置。 如果不为移动的工作表指定位置，Excel 将创建新的工作簿来容纳它。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在文档级自定义项中移动工作表  
  
1.  将工作簿中的工作表的总数分配给一个变量，然后移动第一个工作表，使其成为最后一个工作表。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#24)]  
  
### 在 VSTO 外接程序中移动工作表  
  
1.  将工作簿中的工作表的总数分配给一个变量，然后移动第一个工作表，使其成为最后一个工作表。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#16)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式隐藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [如何：以编程方式从工作簿中删除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以编程方式保护工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)  
  
  