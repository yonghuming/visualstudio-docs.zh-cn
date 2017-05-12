---
title: "Office 解决方案中的后期绑定"
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
  - "对象 [Visual Studio 中的 Office 开发]，强制转换"
  - "类型 [Visual Studio 中的 Office 开发]，强制转换"
  - "自动化 [Visual Studio 中的 Office 开发]，强制转换对象"
  - "强制转换，对象到特定类型"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Office 解决方案中的后期绑定
  Office 应用程序的对象模型中的某些类型提供了可通过后期绑定功能使用的功能。  例如，某些方法和属性可以根据 Office 应用程序的上下文返回不同类型的对象，而某些类型可以在不同的上下文中公开不同的方法或属性。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic 项目 **Option Strict** 位置关闭，并且 Visual C\# 项目目标 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 能直接使用这些后期绑定功能的类型一起使用。  
  
## 对象返回值的隐式和显式强制转换  
 Microsoft Office 主互操作程序集 \(PIA\) 中的许多方法和属性都返回 <xref:System.Object> 值，因为它们能够返回一些不同类型的对象。  例如，<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> 属性返回 <xref:System.Object>，因为其返回值可以为 <xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.Chart> 对象，具体情况视活动工作表而定。  
  
 当方法或属性返回 <xref:System.Object>时，必须显式转换 \(在 Visual Basic 中\) 为正确的对象输入 **Option Strict** 打开状态的 Visual Basic 项目。  您无需显式转换 <xref:System.Object> 返回在 **Option Strict** 关闭状态的 Visual Basic 项目的值。  
  
 大多数情况下，参考文档为返回 <xref:System.Object> 的成员列出了返回值的可能类型。  通过转换或强制转换对象，可以在代码编辑器中为该对象启用 IntelliSense 功能。  
  
 有关在 Visual Basic 中转换的信息，请参见[隐式转换和显式转换 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)和 [CType 函数 &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function)。  
  
### 示例  
 下面的代码示例演示如何转换为特定的对象输入 **Option Strict** 打开状态的 Visual Basic 项目。  此项目类型，您必须显式强制转换 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 属性设置为 <xref:Microsoft.Office.Interop.Excel.Range>。  此示例需要一个带有名为 `Sheet1` 的工作表类的文档级 Excel 项目。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 下面的代码示例演示如何将对象隐式强制转换为 **Option Strict** 处于关闭状态的 Visual Basic 项目或面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Visual C\# 项目中的特定类型。  在这些类型的项目中，<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 属性将隐式强制转换为 <xref:Microsoft.Office.Interop.Excel.Range>。  此示例需要一个带有名为 `Sheet1` 的工作表类的文档级 Excel 项目。  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## 访问只能通过后期绑定使用的成员  
 Office PIA 中的某些属性和方法只能通过后期绑定使用。  在 Visual Basic 在这些语言项目 **Option Strict** 或在 Visual C\# 项目面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的位置，可以使用后期绑定功能来访问后期绑定的成员。  在 Visual Basic 项目 **Option Strict** 位置打开，您必须使用反射来访问这些成员。  
  
### 示例  
 下面的代码示例演示如何在 **Option Strict** 处于关闭状态的 Visual Basic 项目或面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Visual C\# 项目中访问后期绑定的成员。  此示例访问 Word 中**“打开文件”**对话框的后期绑定 **Name** 属性。  若要使用此示例，请从 Word 项目内的 `ThisDocument` 或 `ThisAddIn` 类中运行此示例。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 下面的代码示例演示如何使用反射来完成 **Option Strict** 打开状态的 Visual Basic 项目中的相同任务。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## 请参阅  
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [使用类型 dynamic（C&#35; 编程指南）](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反射（C&#35; 和 Visual Basic）](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  