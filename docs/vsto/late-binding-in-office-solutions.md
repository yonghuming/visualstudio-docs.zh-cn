---
title: "Office 解决方案中的后期绑定 |Microsoft 文档"
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
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 932a7ccc3f52d80e4f75999f401c61b2663095f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="late-binding-in-office-solutions"></a>Office 解决方案中的后期绑定
  Office 应用程序的对象模型中的某些类型提供可通过后期绑定功能的功能。 例如，一些方法和属性可以返回不同类型的具体取决于 Office 应用程序，上下文对象，并且某些类型可以公开不同的方法或在不同上下文中的属性。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic 项目的位置**Option Strict**是关闭和 Visual C# 项目面向[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]可以直接处理采用这些后期绑定功能的类型。  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>对象的返回值的隐式和显式强制转换  
 许多方法和属性在 Microsoft Office 主互操作程序集 (Pia) 返回<xref:System.Object>值，因为它们可以返回多个不同类型的对象。 例如，<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A>属性返回<xref:System.Object>因为其返回值可以是<xref:Microsoft.Office.Interop.Excel.Worksheet>或<xref:Microsoft.Office.Interop.Excel.Chart>对象，具体取决于活动的工作表是什么。  
  
 当方法或属性返回<xref:System.Object>，你必须显式 （在 Visual Basic 中) 将对象转换为 Visual Basic 项目中的正确类型其中**Option Strict**上。 不需要显式强制转换<xref:System.Object>Visual Basic 项目中返回值其中**Option Strict**处于关闭状态。  
  
 在大多数情况下，参考文档列出了可能的返回值类型返回的成员<xref:System.Object>。 转换或的对象强制转换为对象在代码编辑器中启用智能感知。  
  
 有关在 Visual Basic 中的转换的信息，请参阅[隐式和显式转换 &#40;Visual Basic &#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)和[CType 函数 &#40;Visual Basic &#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>示例  
 下面的代码示例演示如何将对象转换为特定类型的 Visual Basic 项目中其中**Option Strict**上。 在此类型的项目，你必须显式转换<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>属性<xref:Microsoft.Office.Interop.Excel.Range>。 此示例中，需要使用一个名为的工作表类的文档级 Excel 项目`Sheet1`。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 下面的代码示例演示如何在 Visual Basic 项目中隐式转换为特定类型的对象其中**Option Strict**关闭或处于的 Visual C# 项目中面向[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 在这些类型的项目，<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>属性隐式强制转换为<xref:Microsoft.Office.Interop.Excel.Range>。 此示例中，需要使用一个名为的工作表类的文档级 Excel 项目`Sheet1`。  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="accessing-members-that-are-available-only-through-late-binding"></a>仅可通过提供后期绑定的成员访问  
 某些属性和 Office Pia 中的方法是仅可通过提供后期绑定。 在 Visual Basic 中项目的位置**Option Strict**是关闭或 Visual C# 项目中面向[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，你可以使用这些语言中的后期绑定功能访问后期绑定成员。 在 Visual Basic 中项目的位置**Option Strict**处于打开状态，你必须使用反射来访问这些成员。  
  
### <a name="examples"></a>示例  
 下面的代码示例演示如何访问 Visual Basic 项目中的后期绑定成员其中**Option Strict**关闭或处于的 Visual C# 项目中面向[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 此示例访问后期绑定**名称**属性**文件打开**在 Word 中的对话框。 若要使用此示例中，运行从`ThisDocument`或`ThisAddIn`Word 项目中的类。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 下面的代码示例演示如何使用反射来完成 Visual Basic 项目中的相同任务其中**Option Strict**上。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>另请参阅  
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)   
 [使用类型 dynamic &#40;使用 c&#35;编程指南 &#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反射 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [反射 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  