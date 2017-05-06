---
title: "如何：以编程方式隐藏工作表"
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
  - "隐藏的工作表"
  - "工作表，隐藏"
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以编程方式隐藏工作表
  可以显示或隐藏工作簿中的任意工作表。 若要隐藏工作表，请使用该工作表宿主项或通过使用工作簿的表集合访问该工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用工作表主机项  
 如果在设计时将工作表添加到了文档级自定义项中，请使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 属性来隐藏指定的工作表。  
  
#### 使用工作表宿主项隐藏工作表  
  
1.  将 `Sheet1` 宿主项的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 属性设置为 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 枚举值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#25)]  
  
## 使用 Excel 工作簿的表集合  
 在下列情况中通过 Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 集合访问工作表：  
  
-   想要隐藏 VSTO 外接程序中的工作表。  
  
-   想要隐藏的工作表是在运行时在文档级自定义项中创建的。  
  
#### 使用 Excel 工作簿的表集合隐藏工作表  
  
1.  将工作表的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> 属性设置为 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 枚举值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#26)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式从工作簿中删除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以编程方式在工作簿中移动工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [如何：以编程方式保护工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)  
  
  