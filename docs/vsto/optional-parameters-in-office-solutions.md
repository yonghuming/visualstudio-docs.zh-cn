---
title: "Office 解决方案中的可选参数"
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
  - "应用程序开发 [Visual Studio 中的 Office 开发], 可选参数"
  - "缺少字段 [Visual Studio 中的 Office 开发]"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 可选参数"
  - "可选参数 [Visual Studio 中的 Office 开发]"
  - "参数 [Visual Studio 中的 Office 开发], 可选"
  - "Visual Basic [Visual Studio 中的 Office 开发], 可选参数"
  - "Visual C# [Visual Studio 中的 Office 开发], 可选参数"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Office 解决方案中的可选参数
  Microsoft Office 应用程序的对象模型中的许多方法都接受可选参数。  如果使用 Visual Basic 在 Visual Studio 中开发 Office 解决方案，你不必为可选参数传递值，因为系统会为每个缺少的参数自动使用默认值。  在大多数情况下，你还可以在 Visual C\# 项目中省略可选参数。 但是，在文档级 Word 项目中，不能省略 `ThisDocument` 类的可选 **ref** 参数。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 有关在 Visual C\# 和 Visual Basic 项目中使用可选参数的详细信息，请参阅[命名实参和可选实参（C&#35; 编程指南）](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments)和[可选参数 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)。  
  
> [!NOTE]  
>  在 Visual Studio 的早期版本中，必须为 Visual C\# 项目中的每个可选参数传递一个值。  为了方便起见，这些项目包括一个名为 `missing` 的全局变量，当你想要使用某个可选参数的默认值时，可以将该变量传递给该可选参数。  在 Visual Studio 中，面向 Office 的 Visual C\# 项目仍然包含 `missing` 变量，但在 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 中开发 Office 解决方案时，通常不需要使用该变量（在面向 Word 的文档级项目中使用 `ThisDocument` 类的可选 **ref** 参数调用方法的情况除外）。  
  
## Excel 中的示例  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法具有多个可选参数。  可以为某些参数指定值，并接受其他参数的默认值，如下面的代码示例所示。  此示例需要一个具有名为 `Sheet1` 的工作表类的文档级项目。  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Word 中的示例  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法具有多个可选参数。  可以为某些参数指定值，并接受其他参数的默认值，如下面的代码示例所示。  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## 在面向 Word 的 Visual C\# 文档级项目中使用 ThisDocument 类中方法的可选参数  
 Word 对象模型包含许多具有可选 **ref** 参数的方法，这些方法接受 <xref:System.Object> 值。  但是，在面向 Word 的 Visual C\# 文档级项目中，不能省略已生成 `ThisDocument` 类的方法的可选 **ref** 参数。  Visual C\# 使你能够仅为接口（而不是类）的方法省略可选的 **ref** 参数。  例如，下面的代码示例无法进行编译，因为不能省略 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> 方法的可选 **ref** 参数。  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 调用 `ThisDocument` 类的方法时，请遵循以下准则：  
  
-   若要接受可选 **ref** 参数的默认值，请将 `missing` 变量传递给该参数。  在 Visual C\# Office 项目中自动定义 `missing` 变量，并分配给生成的项目代码中的值 <xref:System.Type.Missing>。  
  
-   若要为可选 **ref** 参数指定你自己的值，请声明一个分配给你要指定的值的对象，然后将该对象传递给该参数。  
  
 下面的代码示例演示如何通过为 *ignoreUppercase* 参数指定值并接受其他参数的默认值来调用 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> 方法。  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 如果要编写在 `ThisDocument` 类中省略方法的可选 **ref** 参数的代码，你也可以选择对 <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> 属性返回的 <xref:Microsoft.Office.Interop.Word.Document> 对象调用同一方法，并省略该方法中的参数。  可以这样做是因为 <xref:Microsoft.Office.Interop.Word.Document> 是接口而不是类。  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 值和引用类型参数的详细信息，请参阅[通过值和通过引用传递参数 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)（适用于 Visual Basic）以及[传递参数（C&#35; 编程指南）](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)。  
  
## 请参阅  
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)  
  
  