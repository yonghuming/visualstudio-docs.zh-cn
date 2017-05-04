---
title: "如何：以编程方式创建新的 Visio 文档 | Microsoft Docs"
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
  - "Visio [Visual Studio 中的 Office 开发]，创建 Visio 文档"
  - "文档 [Visual Studio 中的 Office 开发]，创建 Visio 文档"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：以编程方式创建新的 Visio 文档
  创建新的 Microsoft Office Visio 绘图文档时，会将其添加到所打开 Visio 文档的 Microsoft.Office.Interop.Visio.Documents 集合中。 随后，Microsoft.Office.Interop.Visio.Documents.Add 方法会创建一个新的 Visio 绘图文档。 有关详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) 方法的 VBA 参考文档。  
  
## 创建新的空白文档  
  
#### 创建新文档  
  
-   使用 Microsoft.Office.Interop.Visio.Documents.Add 方法创建一个不基于模板的新空白文档。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## 创建从现有文档复制而来的文档  
 Microsoft.Office.Interop.Visio.Documents.Add 方法可创建从现有 Visio 文档复制而来的新文档。 你必须提供相应关系图的文件名和完全限定路径。  
  
#### 创建从现有文档复制而来的新文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Add 方法并指定 Visio 关系图的路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## 创建从现有模具复制而来的模具  
 [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) 方法可创建从现有 Visio 模具复制而来的新模具。 你必须提供相应模具的文件名和完全限定路径。  
  
#### 创建从现有模具复制而来的新模具  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Add 方法并指定相应模具的路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 创建基于现有模板的文档  
 Microsoft.Office.Interop.Visio.Documents.Add 方法可创建基于现有 Visio 模板（.vst 文件）的新文档（.vsd 文件）。 此方法会复制作为模板工作区一部分的模具、样式和设置。 你必须提供模板的文件名称和完全限定路径。  
  
#### 创建基于现有模板的新文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Add 方法并指定相应模板的路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## 编译代码  
 此代码示例要求满足以下条件：  
  
-   必须有一个名为 `myDrawing.vsd` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
-   必须有一个名为 `myStencil.vss` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
-   必须有一个名为 `myTemplate.vst` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
## 请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [如何：以编程方式打开 Visio 文档](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何：以编程方式关闭 Visio 文档](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  