---
title: "如何：以编程方式打开 Visio 文档"
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
  - "文档 [Visual Studio 中的 Office 开发]，打开 Visio 文档"
  - "Visio [Visual Studio 中的 Office 开发]，打开 Visio 文档"
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：以编程方式打开 Visio 文档
  打开现有 Microsoft Office Visio 文档的方法有两种：Open 和 OpenEx。OpenEx 方法与 Open 方法相同，但它提供调用方可以在其中指定文档打开方式的参数。  
  
 有关对象模型的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Open](HV10070351) 方法和 [Microsoft.Office.Interop.Visio.Documents.OpenEx](HV10071456) 方法的 VBA 参考文档。  
  
## 打开 Visio 文档  
  
#### 若要打开 Visio 文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Open 方法并提供 Visio 文档的完全限定路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## 使用指定参数打开 Visio 文档  
  
#### 如要以只读和停靠方式打开 Visio 文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.OpenEx 方法，提供 Visio 文档的完全限定路径，并包括想要使用的参数，在本例中为 Docked 和 Read\-only。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
## 编译代码  
 此代码示例要求满足以下条件：  
  
-   必须有一个名为 `myDrawing.vsd` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
## 请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [如何：以编程方式创建新的 Visio 文档](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以编程方式关闭 Visio 文档](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  