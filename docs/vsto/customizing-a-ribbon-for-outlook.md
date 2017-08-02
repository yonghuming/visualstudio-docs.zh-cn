---
title: "自定义 Outlook 功能区"
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
  - "自定义功能区, 关于自定义功能区"
  - "自定义功能区, 关于自定义功能区"
  - "检查器 [Visual Studio 中的 Office 开发]"
  - "Outlook [Visual Studio 中的 Office 开发], 功能区"
  - "功能区 [Visual Studio 中的 Office 开发], Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 自定义 Outlook 功能区
  在 Microsoft Office Outlook 中自定义功能区时，必须考虑自定义功能区在应用程序中出现的位置。  在主应用程序用户界面 \(UI\) 和用户执行某些任务（例如创建电子邮件消息）时打开的窗口中，Outlook 会显示功能区。  这些应用程序窗口被命名为检查器。  
  
 ![链接到视频](~/data-tools/media/playvideo.gif "链接到视频") 有关相关视频演示，请参阅[如何实现：使用功能区设计器在 Outlook 中自定义功能区](http://go.microsoft.com/fwlink/?LinkID=130312)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 将自定义功能区添加到主应用程序 UI  
 主应用程序 UI 在 Outlook 中被称为资源管理器。  如果使用的是**“功能区（可视化设计器）”**项，则可以通过单击**“属性”**窗口中的 **RibbonType** 属性并选择 **Microsoft.Outlook.Explorer** 将功能区添加到资源管理器。  
  
## 将功能区分配给检查器  
 通过指定与该检查器 message 类相对应的功能区类型来确定要进行自定义的检查器。  
  
 如果使用的是**“功能区（可视化设计器）”**项，则可以单击**“属性”**窗口中功能区的 **RibbonType** 属性，然后从值列表中选择一个或多个功能区 ID。  
  
 可以向项目添加多个功能区。  如果多个功能区共享一个功能区 ID，请重写项目的 `ThisAddin` 类中的 CreateRibbonExtensibilityObject 方法，以指定要在运行时显示的功能区。  有关详细信息，请参阅[功能区概述](../vsto/ribbon-overview.md)。  有关每个功能区类型的详细信息，请参阅技术文章[自定义 Outlook 2007 中的功能区](http://msdn.microsoft.com/zh-cn/946e97ea-f556-4e84-8fac-01cd9214e170)。  
  
## 使用功能区 XML 指定功能区类型  
 如果使用的是**“功能区 \(XML\)”**项，请检查 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 方法中 *ribbonID* 参数的值，并返回相应的功能区。  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 方法由 Visual Studio 在功能区代码文件中自动生成。  *ribbonID* 参数是一个标识资源管理器或检查器的特定类型的字符串。  有关 *ribbonID* 参数可能值的完整列表，请参阅技术文章[自定义 Outlook 2007 中的功能区](http://msdn.microsoft.com/zh-cn/946e97ea-f556-4e84-8fac-01cd9214e170)。  
  
 以下代码示例演示如何仅在 `Microsoft.Outlook.Mail.Compose` 检查器中显示自定义功能区。  这是用户创建新的电子邮件时将打开的检查器。  要显示的功能区在 `GetResourceText()` 方法中指定，该方法在 **Ribbon** 类中生成。  有关 **Ribbon** 类的详细信息，请参阅[功能区 XML](../vsto/ribbon-xml.md)。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## 请参阅  
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)  
  
  