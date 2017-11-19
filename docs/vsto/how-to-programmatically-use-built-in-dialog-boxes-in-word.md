---
title: "如何： 以编程方式使用 Word 中的内置对话框 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dd7d81837699aedd1c6c61d0cb0d9e2e9a64db4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>如何：以编程方式使用 Word 中的内置对话框
  当使用 Microsoft Office Word 时，有需要来显示对话框，用户输入的时间。 尽管可以创建你自己，但可能还想要采用的方法使用的内置对话框在 Word 中，它们都公开在<xref:Microsoft.Office.Interop.Word.Dialogs>集合<xref:Microsoft.Office.Interop.Word.Application>对象。 这使您能够访问的内置对话框框中，作为枚举表示的 200。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>显示对话框  
 若要显示一个对话框，使用的值之一<xref:Microsoft.Office.Interop.Word.WdWordDialog>枚举，以创建<xref:Microsoft.Office.Interop.Word.Dialog>对象，表示你想要显示的对话框。 然后，调用<xref:Microsoft.Office.Interop.Word.Dialog.Show%2A>方法<xref:Microsoft.Office.Interop.Word.Dialog>对象。  
  
 下面的代码示例演示如何显示**文件打开**对话框。 若要使用此示例中，运行从`ThisDocument`或`ThisAddIn`项目中的类。  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>访问对话框成员可通过后期绑定  
 某些属性和 Word 中的对话框的方法是仅可通过提供后期绑定。 在 Visual Basic 中项目的位置**Option Strict**处于打开状态，你必须使用反射来访问这些成员。 有关更多信息，请参见 [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md)。  
  
 下面的代码示例演示如何使用**名称**属性**文件打开**在 Visual Basic 中的对话框中项目的位置**Option Strict**关闭或 Visual C# 中项目面向[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]。 若要使用此示例中，运行从`ThisDocument`或`ThisAddIn`项目中的类。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 下面的代码示例演示如何使用反射来访问**名称**属性**文件打开**在 Visual Basic 中的对话框中项目的位置**Option Strict**是上。 若要使用此示例中，运行从`ThisDocument`或`ThisAddIn`项目中的类。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式使用在隐藏模式下的 Word 对话框](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反射 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [反射 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  