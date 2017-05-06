---
title: "如何：以编程方式打开工作簿"
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
  - "Excel [Visual Studio 中的 Office 开发], 打开工作簿"
  - "工作簿, 打开"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 如何：以编程方式打开工作簿
  Microsoft Office Excel 中的 <xref:Microsoft.Office.Interop.Excel.Workbooks> 集合使您能够使用所有打开的工作簿和打开工作簿。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 打开现有工作簿  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Workbooks> 集合的 <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> 方法，传入工作簿的路径。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## 编译代码  
 此代码示例要求满足以下条件：  
  
-   名为 `YourWorkbook.xls` 的工作簿必须存在于驱动器 C 上的 `Test` 目录中。  
  
## 请参阅  
 [使用工作簿](../vsto/working-with-workbooks.md)   
 [如何：以编程方式及工作簿形式打开文本文件](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [如何：以编程方式新建工作簿](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [如何：以编程方式保存工作簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何：以编程方式关闭工作簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
  