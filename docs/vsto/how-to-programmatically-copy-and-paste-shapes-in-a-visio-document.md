---
title: "如何：以编程方式在 Visio 文档中复制和粘贴形状 | Microsoft Docs"
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
  - "形状 [Visual Studio 中的 Office 开发]，复制和粘贴 Visio 形状"
  - "Visio [Visual Studio 中的 Office 开发]，复制和粘贴 Visio 形状"
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：以编程方式在 Visio 文档中复制和粘贴形状
  你可以以编程方式复制文档中某一页上的形状，并将其粘贴到同一文档中新的一页。 你可以选择将其粘贴到默认位置（活动窗口的中央），或将其粘贴到与在其原始页相同的坐标位置。  
  
## 复制和粘贴形状  
 有关对象模型的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304)、[Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300)、[Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) 和 [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](HV10071835) 标志的 VBA 参考文档。  
  
#### 将形状复制到另一页的中央  
  
-   下面的示例演示如何复制第一页中的形状并将其粘贴到第二页的中央。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
## 复制形状并粘贴到相同的位置  
 有关对象模型的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304)、[Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300)、[Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) 和 [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](HV10071835) 标志的 VBA 参考文档。  
  
 如果你需要控制所粘贴信息的格式并建立到源文件（例如，Microsoft Office Word 文档）的链接（可选），请使用 PasteSpecial 方法。  
  
#### 将形状和形状位置复制到另一页  
  
-   下面的示例演示如何复制第一页中的形状并将其粘贴到第二页中与其原始坐标相同的位置。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## 请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [使用 Visio 形状](../vsto/working-with-visio-shapes.md)   
 [如何：以编程方式向 Visio 文档中添加形状](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  