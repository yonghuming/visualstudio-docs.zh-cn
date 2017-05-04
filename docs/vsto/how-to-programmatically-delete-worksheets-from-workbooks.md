---
title: "如何：以编程方式从工作簿中删除工作表 | Microsoft Docs"
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
  - "工作簿, 删除工作表"
  - "工作表, 删除"
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以编程方式从工作簿中删除工作表
  可以删除工作簿中的任意工作表。  若要删除工作表，请使用该工作表主机项或通过使用工作簿的表集合访问该工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用工作表主机项  
 如果在设计时将工作表添加到了文档级自定义项，请使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 方法来删除指定的工作表。  下列代码通过直接引用工作表主机项从工作簿中删除工作表。  
  
> [!IMPORTANT]  
>  此代码仅在使用下列任意项目模板创建的项目中运行：  
>   
>  -   Excel 2013 工作簿  
> -   Excel 2013 模板  
> -   Excel 2010 工作簿  
> -   Excel 2010 模板  
>   
>  如果想在其他任意类型的项目中执行此任务，必须先添加对 **Microsoft.Office.Interop.Excel** 程序集的引用，然后必须使用该程序集的类来打开工作簿或删除工作表。  有关详细信息，请参阅[如何：通过主互操作程序集面向 Office 应用程序](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)和 [Excel 2010 主互操作程序集引用](http://go.microsoft.com/fwlink/?LinkId=189585)。  
  
#### 使用工作表主机项删除工作表  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 的 `Sheet1` 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#17)]  
  
## 使用 Excel 工作簿的表集合  
 在下列情况中通过 Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 集合访问工作表：  
  
-   想要删除 VSTO 外接程序中的工作表。  
  
-   想要删除的工作表是在运行时文档级自定义项中创建的。  
  
 下列代码通过从 **Sheets** 集合的索引号引用工作表来删除工作薄中的该表。  此代码假定以编程方式创建了一个新工作表。  
  
> [!IMPORTANT]  
>  如果想在其他任意类型的项目中执行此任务，必须先添加对 **Microsoft.Office.Interop.Excel** 程序集的引用，然后必须使用该程序集的类来打开工作簿或删除工作表。  有关详细信息，请参阅[如何：通过主互操作程序集面向 Office 应用程序](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)和 [Excel 2010 主互操作程序集引用](http://go.microsoft.com/fwlink/?LinkId=189585)。  
  
#### 使用 Excel 工作簿的表集合删除工作表  
  
1.  调用 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#18)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式隐藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [如何：以编程方式在工作簿中移动工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [如何：以编程方式选择工作表](../vsto/how-to-programmatically-select-worksheets.md)   
 [如何：以编程方式向工作簿添加新工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [工作表宿主项](../vsto/worksheet-host-item.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  