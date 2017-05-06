---
title: "如何：以编程方式使用 Word 中的内置对话框"
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
  - "Word [Visual Studio 中的 Office 开发]，对话框"
  - "对话框，Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 如何：以编程方式使用 Word 中的内置对话框
  使用 Microsoft Office Word 时，有时需要显示用户输入对话框。  虽然可以创建自己的对话框，您也许还希望采用使用 Word 中内置对话框的方法，这些对话框在 <xref:Microsoft.Office.Interop.Word.Application> 对象的 <xref:Microsoft.Office.Interop.Word.Dialogs> 集合中公开。  这使您能够访问 200 个以上的内置对话框，它们以枚举的形式表示。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 显示对话框  
 若要显示对话框，请使用 <xref:Microsoft.Office.Interop.Word.WdWordDialog> 枚举的值之一来创建 <xref:Microsoft.Office.Interop.Word.Dialog> 对象，该对象表示要显示的对话框。  然后，调用 <xref:Microsoft.Office.Interop.Word.Dialog> 对象的 <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> 方法。  
  
 下面的代码示例演示如何显示**“打开”**对话框。  若要使用此示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### 访问可通过后期绑定使用的对话框成员  
 Word 中对话框的某些属性和方法只能通过后期绑定使用。  在 Visual Basic 项目 **Option Strict** 位置打开，您必须使用反射来访问这些成员。  有关更多信息，请参见[Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)。  
  
 下面的代码示例在 **Option Strict** 或在 Visual C\# 项目面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Visual Basic 项目演示如何使用 **文件已打开** 对话框的 **Name** 属性。  若要使用此示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 下面的代码示例演示如何使用反射来 **文件已打开** 对话框 **Name** 属性在 Visual Basic 中的项目的访问 **Option Strict** 位置打开。  若要使用此示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## 请参阅  
 [如何：以编程方式在隐藏模式下使用 Word 对话框](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反射（C&#35; 和 Visual Basic）](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  