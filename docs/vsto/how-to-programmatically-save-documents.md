---
title: "如何：以编程方式保存文档"
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
  - "文档 [Visual Studio 中的 Office 开发], 保存"
  - "Word [Visual Studio 中的 Office 开发], 保存文档"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以编程方式保存文档
  可通过多种方式保存 Microsoft Office Word 文档。  您可以保存文档而不更改文档的名称，也可以用新名称保存文档。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 保存文档而不更改名称  
  
#### 保存与文档级自定义项关联的文档  
  
1.  调用 <xref:Microsoft.Office.Tools.Word.Document> 类的 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 方法。  若要使用此代码示例，请从项目内的 `ThisDocument` 类中运行此示例。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### 保存活动文档  
  
1.  调用活动文档的 <xref:Microsoft.Office.Interop.Word._Document.Save%2A> 方法。  若要使用此代码示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 如果不确定要保存的文档是否是活动文档，可以使用文档名引用该文档。  
  
#### 保存通过名称指定的文档  
  
1.  将文档名作为 <xref:Microsoft.Office.Interop.Word.Documents> 集合的参数。  若要使用此代码示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## 用新名称保存文档  
 使用 SaveAs 方法可以用新名称保存文档。  您可以在文档级 Word 项目中使用 <xref:Microsoft.Office.Tools.Word.Document> 宿主项中的此方法，也可以在任何 Word 项目中使用本机 <xref:Microsoft.Office.Interop.Word.Document> 对象的此方法。  此方法要求指定新的文件名，但其他参数是可选的。  
  
> [!NOTE]  
>  如果在 `ThisDocument` 的 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件处理程序内显示**“另存为”**对话框，并且将 *Cancel* 参数设置为 **false**，则应用程序可能会意外退出。  如果将 *Cancel* 参数设置为 **true**，将显示一条错误信息，指示 Autosave 已禁用。  
  
#### 用新名称保存与文档级自定义项关联的文档  
  
1.  使用完全限定的路径和文件名调用项目中 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> 方法。  如果该文件夹中已存在同名称的文件，则会覆盖该文件而不显示任何提示。  若要使用此代码示例，请从 `ThisDocument` 类中运行它。  
  
    > [!NOTE]  
    >  如果目标目录不存在或者在保存文件时发生其他问题，则 <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> 方法将引发异常。  好的做法是，在 <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> 方法前后或在一个调用方法内部使用 **try…catch** 块。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### 用新名称保存本机文档  
  
1.  使用完全限定的路径和文件名，调用想要保存的 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 方法。  如果该文件夹中已存在同名称的文件，则会覆盖该文件而不显示任何提示。  
  
     下面的代码示例用新名称保存活动文档。  若要使用此代码示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
    > [!NOTE]  
    >  如果目标目录不存在或者保存文件时有其他问题，<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 方法将引发异常。  好的做法是，在 <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 方法前后或在一个调用方法内部使用 **try…catch** 块。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## 编译代码  
 此代码示例要求满足以下条件：  
  
-   若要使用名称保存文档，驱动器 C 上名为 Test 的目录中必须存在一个名为 NewDocument.doc 的文档。  
  
-   若要使用新名称保存文档，驱动器 C 上必须存在一个名为 Test 的目录。  
  
## 请参阅  
 [如何：以编程方式关闭文档](../vsto/how-to-programmatically-close-documents.md)   
 [如何：以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [文档宿主项](../vsto/document-host-item.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  