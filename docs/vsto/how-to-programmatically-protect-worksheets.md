---
title: "如何：以编程方式保护工作表 | Microsoft Docs"
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
  - "文档保护, 添加到工作表"
  - "文档 [Visual Studio 中的 Office 开发], 文档保护"
  - "保护, 添加到工作表"
  - "工作表, 保护"
ms.assetid: 50bde1ff-918a-42ca-ba1b-f22139f8717a
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：以编程方式保护工作表
  Microsoft Office Excel 中的保护功能可帮助防止用户和代码修改工作表中的对象。  默认情况下，开启保护之后，将锁定所有单元格。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 在文档级自定义项中，可以通过使用 Excel 设计器来保护工作表。  还可以在运行时以编程方式保护任何项目类型中的工作表。  
  
> [!NOTE]  
>  无法将 Windows 窗体控件添加到受保护工作表的区域中。  
  
## 使用设计器  
  
#### 若要在设计器中保护工作表  
  
1.  在**“审阅”**选项卡的**“更改”**组中，单击**“保护工作表”**。  
  
     **“保护工作表”**对话框随即出现。  可以设置密码，并根据需要指定用户可利用工作表执行的特定操作，例如设置单元格格式或插入行。  
  
 还可以允许用户编辑受保护工作表中的特定范围。  
  
#### 若要允许在特定范围内编辑  
  
1.  在**“审阅”**选项卡的**“更改”**组中，单击**“允许用户编辑范围”**。  
  
     **“允许用户编辑范围”**对话框随即出现。  可以指定使用密码解锁的范围，以及指定不需要密码就可以编辑范围的用户。  
  
## 在运行时使用代码  
 下面的代码会设置密码（使用变量 getPasswordFromUser，其中包含从用户处获得的密码），并仅允许排序。  
  
#### 若要通过在文档级自定义项中使用代码来保护工作表  
  
1.  调用工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> 方法。  此示例假定你正在使用名为 `Sheet1` 的工作表。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#27)]  
  
#### 若要通过在 VSTO 外接程序中使用代码来保护工作表  
  
1.  调用活动工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#17)]  
  
## 请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以编程方式取消工作表保护](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [如何：以编程方式保护工作簿](../vsto/how-to-programmatically-protect-workbooks.md)   
 [如何：以编程方式隐藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [工作表宿主项](../vsto/worksheet-host-item.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  