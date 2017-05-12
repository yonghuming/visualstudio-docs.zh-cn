---
title: "如何：以编程方式保存 Visio 文档"
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
  - "文档 [Visual Studio 中的 Office 开发]，保存 Visio 文档"
  - "Visio [Visual Studio 中的 Office 开发]，保存 Visio 文档"
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：以编程方式保存 Visio 文档
  可通过几种方法来保存 Microsoft Office Visio 文档：  
  
-   将更改保存在现有文档中。  
  
-   保存新文档，或使用新名称保存文档。  
  
-   使用指定参数保存文档。  
  
 有关详细信息，请参阅 [Microsoft.Office.Interop.Visio.Document.Save](HV10071468) 方法、[Microsoft.Office.Interop.Visio.Document.SaveAs](HV10071469) 方法和 [Microsoft.Office.Interop.Visio.Document.SaveAsEx](HV10071470) 方法的 VBA 参考文档。  
  
## 保存现有文档  
  
#### 保存文档  
  
-   调用以前保存的文档的 Microsoft.Office.Tools.Visio.Document 类的 Microsoft.Office.Interop.Visio.Document.Save 方法。  
  
     若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
    > [!NOTE]  
    >  如果尚未保存新 Visio 文档，则 Microsoft.Office.Interop.Visio.Document.Save 方法会引发异常。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
## 使用新名称保存文档  
 使用 Microsoft.Office.Interop.Visio.Document.SaveAs 方法可保存新文档或具有新名称的文档。 此方法要求指定新文件名。  
  
#### 使用新名称保存活动 Visio 文档  
  
-   使用包括文件名的完全限定路径来调用要保存的 Microsoft.Office.Tools.Visio.Document 的 Microsoft.Office.Interop.Visio.Document.SaveAs 方法。 如果该文件夹中已存在具有该名称的文件，则以无提示方式覆盖它。  
  
     若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## 使用新名称和指定参数保存文档  
 使用 Microsoft.Office.Interop.Visio.Document.SaveAsEx 方法可使用新名称保存文档，并指定要应用于该文档的任何适用参数。  
  
#### 若要使用新名称和指定参数保存文档  
  
-   使用包括文件名的完全限定路径来调用要保存的 Microsoft.Office.Tools.Visio.Document 的 Microsoft.Office.Interop.Visio.Document.SaveAsEx 方法。 如果该文件夹中已存在具有该名称的文件，则引发异常。  
  
     下面的代码示例使用新名称保存活动文档，将文档标记为只读，并在“最近使用过的”文档列表中显示文档。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## 编译代码  
 此代码示例要求满足以下条件：  
  
-   要保存具有新名称的文档，必须有一个名为 `Test` 的目录位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中。  
  
## 请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [如何：以编程方式创建新的 Visio 文档](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以编程方式打开 Visio 文档](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何：以编程方式关闭 Visio 文档](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  