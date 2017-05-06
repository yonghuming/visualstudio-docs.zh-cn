---
title: "在运行时访问功能区"
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
  - "全局类, 功能区"
  - "功能区 [Visual Studio 中的 Office 开发], 访问"
  - "RibbonManager 类"
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 在运行时访问功能区
  可编辑代码以显示、隐藏和修改功能区以及使用户能够从自定义任务窗格、操作窗格或 Outlook 窗体区域中的控件运行代码。  
  
 可以通过使用 `Globals` 类来访问功能区。  对于 Outlook 项目，可以访问在特定 Outlook 检查器或 Outlook 资源管理器窗口中显示的功能区。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## 使用 Globals 类访问功能区  
 可以使用 `Globals` 类从项目中的任何位置访问文档级项目或 VSTO 外接程序项目中的功能区。  
  
 有关 `Globals` 类的详细信息，请参阅[对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)。  
  
 下面的示例使用 `Globals` 类来访问名为 `Ribbon1` 的自定义功能区，并将在功能区中组合框上显示的文本设置为 `Hello World`。  
  
 [!code-csharp[Trin_Outlook_FR_Access#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#4)]
 [!code-vb[Trin_Outlook_FR_Access#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#4)]  
  
## 访问在特定 Outlook 检查器窗口中显示的功能区的集合  
 可以访问在 Outlook*“检查器”*中显示的功能区的集合。  检查器是在用户执行某些任务时（例如创建电子邮件）打开的 Outlook 窗口。  若要访问检查器窗口的功能区，请调用 `Globals` 类的 `Ribbons` 属性，并传入表示该检查器的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 对象。  
  
 下面的示例获取当前位于最前的检查器的功能区集合。  此示例随后访问名为 `Ribbon1` 的功能区，并将功能区的组合框上显示的文本设置为 `Hello World`。  
  
 [!code-csharp[Trin_Outlook_FR_Access#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#5)]
 [!code-vb[Trin_Outlook_FR_Access#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#5)]  
  
## 访问在特定 Outlook 资源管理器中显示的功能区的集合  
 可以访问在 Outlook*“资源管理器”*中显示的功能区的集合。  资源管理器是 Outlook 实例的主要应用程序用户界面 \(UI\)。  若要访问资源管理器窗口的功能区，请调用 `Globals` 类的 `Ribbons` 属性，并传入表示该资源管理器的 <xref:Microsoft.Office.Interop.Outlook.Explorer> 对象。  
  
 下面的示例获取当前位于最前的资源管理器的功能区集合。  此示例随后访问名为 `Ribbon1` 的功能区，并将功能区的组合框上显示的文本设置为 `Hello World`。  
  
 [!code-csharp[Trin_Outlook_FR_Access#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#6)]
 [!code-vb[Trin_Outlook_FR_Access#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#6)]  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [功能区对象模型概述](../vsto/ribbon-object-model-overview.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：在运行时更新功能区上的控件](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)   
 [在运行时访问窗体区域](../vsto/accessing-a-form-region-at-run-time.md)  
  
  