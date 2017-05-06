---
title: "如何：以编程方式保存工作簿"
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
  - "工作簿, 保存"
  - "工作簿, 保存备份副本"
  - "工作簿, 以 XML 格式保存"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 如何：以编程方式保存工作簿
  可通过多种方式保存工作簿。  可以保存工作簿而不更改路径。  如果以前没有保存过工作簿，则应该通过指定一个路径来保存工作簿。  如果没有显式路径，Microsoft Office Excel 会使用创建文件时为其指定的名称将文件保存在当前文件夹中。  还可以保存工作簿的副本，而不修改内存中打开的工作簿。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 保存工作簿而不更改路径  
  
#### 保存与文档级自定义项关联的工作簿  
  
1.  调用 ThisWorkbook 类的 <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### 在 VSTO 外接程序中保存活动工作簿  
  
1.  调用 <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> 方法以保存活动工作薄。  若要使用下面的代码示例，请在 Excel 的应用程序级项目内的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 使用新路径保存工作簿  
 可以将指定的工作簿保存到新位置或以新名称保存，还可以选择指定文件格式、密码和访问模式等。  
  
> [!NOTE]  
>  在使用新路径保存工作簿之前，你可能要将 <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> 属性设置为 **False**，因为以某些格式保存时需要交互操作。  将此属性设置为 **False** 后，Excel 会全部使用默认值。  
  
#### 保存与文档级自定义项关联的工作簿  
  
1.  调用 `ThisWorkbook` 类的 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 方法。  若要使用下面的代码示例，请在 `ThisWorkbook` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### 在 VSTO 外接程序中保存活动工作簿  
  
1.  调用 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> 方法以将活动工作簿保存到新路径。  若要使用下面的代码示例，请在 Excel 的应用程序级项目内的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## 保存工作簿的副本  
 可以将工作簿的副本保存到文件中，而不修改内存中打开的工作簿。  当想要创建备份副本而不修改工作簿的位置时，此方法十分有用。  
  
#### 保存与文档级自定义项关联的工作簿  
  
1.  调用 `ThisWorkbook` 类的 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> 方法。  若要使用下面的代码示例，请在 `ThisWorkbook` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### 在 VSTO 外接程序中保存活动工作簿  
  
1.  调用 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> 方法以保存活动工作簿的副本。  若要使用下面的代码示例，请在 Excel 的应用程序级项目内的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## 可靠编程  
 以交互方式取消任何保存或复制工作簿的方法将在代码中引发运行时错误。  例如，如果过程调用了 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 方法但未禁用 Excel 提示，则用户在出现的提示中单击**“取消”**时，Excel 将引发一个运行时错误。  
  
## 请参阅  
 [使用工作簿](../vsto/working-with-workbooks.md)   
 [工作簿宿主项](../vsto/workbook-host-item.md)   
 [如何：以编程方式关闭工作簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
  