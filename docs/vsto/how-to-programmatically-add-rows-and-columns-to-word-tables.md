---
title: "如何：以编程方式向 Word 表中添加行和列 | Microsoft Docs"
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
  - "列 [Visual Studio 中的 Office 开发], 添加到 Word 表"
  - "行 [Visual Studio 中的 Office 开发], 添加到 Word 表"
  - "表 [Visual Studio 中的 Office 开发], 添加行和列"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 如何：以编程方式向 Word 表中添加行和列
  在 Microsoft Office Word 表中，单元格组织为行和列。  你可以使用 <xref:Microsoft.Office.Interop.Word.Rows> 对象的 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法将行添加到表，并可以使用 <xref:Microsoft.Office.Interop.Word.Columns> 对象的 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法添加列。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 文档级自定义项示例  
 可以在文档级自定义项中使用下列代码示例。  若要使用这些示例，请从项目中的 `ThisDocument` 类运行它们。  这些示例假定与你的自定义相关联的文档已具有至少一个表。  
  
> [!IMPORTANT]  
>  此代码仅在使用下列任意项目模板创建的项目中运行：  
>   
>  -   Word 2013 文档  
> -   Word 2013 模板  
> -   Word 2010 文档  
> -   Word 2010 模板  
>   
>  如果你想要在其他任意类型的项目中执行此任务，则必须添加对 **Microsoft.Office.Interop.Word** 程序集的引用，然后必须使用该程序集的类向表添加行和列。  有关详细信息，请参阅[如何：通过主互操作程序集面向 Office 应用程序](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)和 [Word 2010 主互操作程序集引用](http://go.microsoft.com/fwlink/?LinkId=189588)。  
  
#### 向表中添加行  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法向表中添加一行。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### 向表中添加列  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法，然后使用 <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> 方法使所有列具有相同的宽度。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## VSTO 外接程序示例  
 可以在 VSTO 外接程序中使用下列代码示例。  若要使用这些示例，请从项目中的 `ThisAddIn` 类运行它们。  这些示例假定活动文档已经具有至少一个表。  
  
> [!IMPORTANT]  
>  此代码仅在你使用 Word VSTO 外接程序模板创建的项目中运行。  
>   
>  如果你想要在其他任意类型的项目中执行此任务，则必须添加对 **Microsoft.Office.Interop.Word** 程序集的引用，然后必须使用该程序集的类向表添加行和列。  有关详细信息，请参阅[如何：通过主互操作程序集面向 Office 应用程序](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)和 [Word 2010 主互操作程序集引用](http://go.microsoft.com/fwlink/?LinkId=189588)。  
  
#### 向表中添加行  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法向表中添加一行。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### 向表中添加列  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法，然后使用 <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> 方法使所有列具有相同的宽度。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## 请参阅  
 [如何：以编程方式创建 Word 表](../vsto/how-to-programmatically-create-word-tables.md)   
 [如何：以编程方式向 Word 表中的单元格添加文本和格式设置](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [如何：以编程方式用文档属性填充 Word 表](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  