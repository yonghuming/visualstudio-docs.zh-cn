---
title: "如何：以编程方式向 Visio 文档中添加形状"
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
  - "Visio [Visual Studio 中的 Office 开发]，添加 Visio 形状"
  - "形状 [Visual Studio 中的 Office 开发]，添加 Visio 形状"
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：以编程方式向 Visio 文档中添加形状
  可以通过从模具中检索主控形状并将形状放置在活动页面上，向 Microsoft Office Visio 文档添加形状。  
  
 有关详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) 方法、[Microsoft.Office.Interop.Visio.Application.ActivePage](HV10069528) 属性和 [Microsoft.Office.Interop.Visio.Page.Drop](HV10070273) 方法的 VBA 参考文档。  
  
## 向 Visio 文档添加形状  
  
#### 若要向 Visio 文档添加形状  
  
-   在文档处于活动状态的情况下，从 Documents.Masters 集合中检索主控形状并将形状放置在活动文档上。 可以使用索引或主控形状名称来检索主控形状。  
  
     下面的代码示例创建一个空白 Visio 文档，然后在“基本形状”模具停靠的情况下打开它。 该代码随后检索多个形状并将它们放置在活动页面上。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## 请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [使用 Visio 形状](../vsto/working-with-visio-shapes.md)   
 [如何：以编程方式在 Visio 文档中复制和粘贴形状](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  