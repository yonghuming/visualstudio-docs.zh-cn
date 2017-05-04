---
title: "如何：以编程方式将工作表中的行分组 | Microsoft Docs"
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
  - "列 [Visual Studio 中的 Office 开发], 取消分组"
  - "组"
  - "组 [Visual Studio 中的 Office 开发], 在工作表中清除"
  - "组, 在工作表中创建"
  - "范围, 创建组"
  - "行 [Visual Studio 中的 Office 开发], 取消分组"
  - "工作表, 清除组"
  - "工作表, 创建组"
  - "工作表, 取消行和列的分组"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以编程方式将工作表中的行分组
  可以对一个或多个整行进行分组。  若要在工作表中创建组，请使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件或本机 Excel 区域对象。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用 NamedRange 控件  
 如果在设计时向文档级项目中添加一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，则可以使用该控件以编程方式创建组。  下面的示例假定同一工作表中有三个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件：`data2001`、`data2002` 和 `dataAll`。  每个命名区域都引用工作表中的一个整行。  
  
#### 在工作表上创建一组 NamedRange 控件  
  
1.  通过调用每个范围的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> 方法将三个命名范围分组。  此代码必须放置在一个表类中，而不是放在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  若要取消对行进行分组，请调用 <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> 方法。  
  
## 使用本机 Excel 范围  
 此代码假定工作表上有三个 Excel 范围，这三个范围的名称分别为 `data2001`、`data2002` 和 `dataAll`。  
  
#### 在工作表内创建一组 Excel 范围  
  
1.  通过调用每个范围的 <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> 方法将三个命名范围分组。  下面的示例假定同一工作表中有三个 <xref:Microsoft.Office.Interop.Excel.Range> 控件，这三个控件的名称分别为 `data2001`、`data2002` 和 `dataAll`。  每个命名区域都引用工作表中的一个整行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  若要取消对行进行分组，请调用 <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> 方法。  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [如何：向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  