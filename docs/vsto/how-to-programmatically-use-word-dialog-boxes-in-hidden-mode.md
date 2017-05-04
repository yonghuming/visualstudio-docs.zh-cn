---
title: "如何：以编程方式在隐藏模式下使用 Word 对话框 | Microsoft Docs"
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
  - "对话框, Word 中的隐藏模式"
  - "隐藏的对话框"
  - "Word [Visual Studio 中的 Office 开发], 对话框"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以编程方式在隐藏模式下使用 Word 对话框
  在 Microsoft Office Word 中，可以使用一个方法调用在不向用户显示的情况下调用内置对话框，从而执行复杂的操作。  通过使用 <xref:Microsoft.Office.Interop.Word.Dialog> 对象的 <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> 方法，而不调用 <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> 方法，就可以执行此操作。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 示例  
 下面的代码示例演示如何在隐藏模式下使用**“页面设置”**对话框在无用户输入的情况下设置多个页面设置属性。  这些示例使用 <xref:Microsoft.Office.Interop.Word.Dialog> 对象来配置自定义页面大小。  页面设置的具体设置（例如上边距、下边距等）以 <xref:Microsoft.Office.Interop.Word.Dialog> 对象的后期绑定属性的形式提供。  这些属性是由 Word 在运行时动态创建的。  
  
 下面的示例演示如何在 **Option Strict** 处于关闭状态的 Visual Basic 项目和面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Visual C\# 项目中执行此任务。  在这些项目中，您可以使用 Visual Basic 和 Visual C\# 编译器中的后期绑定功能。  若要使用此示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 下面的示例在 **Option Strict** 打开状态的 Visual Basic 项目演示如何执行此任务。  在这些项目中，您必须使用反射来访问后期绑定的属性。  若要使用此示例，请从项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## 请参阅  
 [如何：以编程方式使用 Word 中的内置对话框](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)   
 [反射（C&#35; 和 Visual Basic）](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)  
  
  