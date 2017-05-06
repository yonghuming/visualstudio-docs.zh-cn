---
title: "对 Office 项目中对象的全局访问"
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
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "全局类，对象全局访问"
  - "工作表 [Visual Studio 中的 Office 开发]，全局访问"
  - "文档 [Visual Studio 中的 Office 开发]，全局访问"
  - "事件处理程序 [Visual Studio 中的 Office 开发]"
  - "ThisWorkbook_Startup"
  - "应用程序级外接程序 [Visual Studio 中的 Office 开发]"
  - "外接程序 [Visual Studio 中的 Office 开发]，事件"
  - "工作薄 [Visual Studio 中的 Office 开发]，全局访问"
  - "ThisWorkbook_Shutdown"
  - "文档级自定义项 [Visual Studio 中的 Office 开发]"
  - "Startup 事件"
  - "Shutdown 事件"
  - "项目 [Visual Studio 中的 Office 开发]，全局访问"
  - "Office 文档 [Visual Studio 中的 Office 开发]，全局访问"
  - "ThisAddin_Startup"
  - "事件 [Visual Studio 中的 Office 开发]"
  - "ThisAddIn_Shutdown"
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# 对 Office 项目中对象的全局访问
  创建 Office 项目时，Visual Studio 将在项目中自动生成一个名为 `Globals` 的类。 可以使用 `Globals` 类在运行时从项目中的任何代码访问多个不同的项目项。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 如何使用全局类  
 `Globals` 是一个静态类，该类将对某些项的引用保留在你的项目中。 通过使用 `Globals` 类，可在运行时从项目中的任何代码访问以下各项：  
  
-   Excel 工作簿或模板项目中的 `ThisWorkbook` 和 `Sheet`*n* 类。 可以通过使用 `Globals.ThisWorkbook` 和 `Sheet`*n* 属性访问这些对象。  
  
-   Word 文档或模板项目中的 `ThisDocument` 类。 可以通过使用 `Globals.ThisDocument` 属性访问此对象。  
  
-   VSTO 外接程序项目中的 `ThisAddIn` 类。 可以通过使用 `Globals.ThisAddIn` 属性访问此对象。  
  
-   项目中通过使用功能区设计器自定义的所有功能区。 可以通过使用 `Globals.Ribbons` 属性访问功能区。 有关详细信息，请参阅[在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)。  
  
-   Outlook VSTO 外接程序项目中的所有 Outlook 窗体区域。 可以通过使用 `Globals.FormRegions` 属性访问这些窗体区域。 有关更多信息，请参见[在运行时访问窗体区域](../vsto/accessing-a-form-region-at-run-time.md)。  
  
-   一个工厂对象，该对象使你可在运行时在面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的项目中创建功能区控件和主机项。 可以通过使用 `Globals.Factory` 属性访问此对象。 此对象是实现以下接口之一的类的实例：  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 例如，当用户单击 Excel 的文档级项目中的操作窗格上的按钮时，你可以使用 `Globals.Sheet1` 属性将文本插入到 `Sheet1` 上的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件中。  
  
 [!code-csharp[Trin_VstcoreProgramming#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstcoreProgramming#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#1)]  
  
## 初始化全局类  
 在完全初始化文档或 VSTO 外接程序之前，尝试使用 `Globals` 类的代码可能引发运行时异常。 例如，声明一个类级变量时使用 `Globals` 可能会失败，因为在对声明的对象进行实例化之前，可能不会使用对所有主机项的引用将 `Globals` 类初始化。  
  
> [!NOTE]  
>  永远不会在设计时初始化 `Globals` 类，控件实例由设计器创建。 这意味着，如果从一个用户控件类的内部创建使用 `Globals` 类的属性的用户控件，则在尝试使用返回的对象之前，必须确定该属性是否返回 **null**。  
  
## 请参阅  
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)   
 [在运行时访问窗体区域](../vsto/accessing-a-form-region-at-run-time.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [文档宿主项](../vsto/document-host-item.md)   
 [工作簿宿主项](../vsto/workbook-host-item.md)   
 [工作表宿主项](../vsto/worksheet-host-item.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)  
  
  