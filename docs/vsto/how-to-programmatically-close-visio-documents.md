---
title: "如何：以编程方式关闭 Visio 文档 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发]，关闭 Visio 文档"
  - "Visio [Visual Studio 中的 Office 开发]，关闭 Visio 文档"
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：以编程方式关闭 Visio 文档
  可以使用 Microsoft.Office.Interop.Visio.Document.Close 方法关闭活动 Microsoft Office Visio 文档。  
  
 有关此方法的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Document.Close](HV10070225) 方法的 VBA 参考文档。  
  
## 关闭活动文档  
  
#### 关闭活动文档  
  
-   调用 Microsoft.Office.Interop.Visio.Document.Close 方法关闭活动文档。  
  
     若要使用以下代码示例，请在 Visio 的 VSTO 外接程序项目内的 `ThisAddIn` 类中运行它。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## 请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [如何：以编程方式创建新的 Visio 文档](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以编程方式打开 Visio 文档](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何：以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  