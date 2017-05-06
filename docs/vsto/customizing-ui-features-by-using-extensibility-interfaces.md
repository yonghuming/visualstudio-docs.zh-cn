---
title: "使用扩展性接口自定义 UI 功能"
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
  - "ICustomTaskPaneConsumer 接口"
  - "IRibbonExtensibility 接口"
  - "UI 自定义 [Visual Studio 中的 Office 开发]"
  - "用户界面 [Visual Studio 中的 Office 开发]，自定义"
  - "应用程序级外接程序 [Visual Studio 中的 Office 开发]，扩展性接口"
  - "自定义 UI 功能 [Visual Studio 中的 Office 开发]"
  - "FormRegionStartup 接口"
  - "外接程序 [Visual Studio 中的 Office 开发]，扩展性接口"
  - "扩展性接口 [Visual Studio 中的 Office 开发]"
ms.assetid: 3f3f7908-9404-4eda-8899-4d18c75e3b4a
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 使用扩展性接口自定义 UI 功能
  Visual Studio 中的 Office 开发工具提供了一些类和设计器，使用它们在 VSTO 外接程序中创建自定义任务窗格、功能区自定义项和 Outlook 窗体区域时可处理许多实现细节。 不过，如果你有特殊要求，也可以自己为每项功能实现*扩展性接口*。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## 扩展性接口概述  
 Microsoft Office 定义了一组扩展性接口，COM VSTO 外接程序可通过实现这些接口来自定义某些功能，例如功能区。 这些接口完全控制可通过其访问的功能。 不过，实现这些接口需要掌握一些有关托管代码中的 COM 互操作性的知识。 在某些情况下，对于熟悉 .NET Framework 的开发人员而言，这些接口的编程模型也并不直观。  
  
 使用 Visual Studio 中的 Office 项目模板创建 VSTO 外接程序时，不必实现扩展性接口来自定义功能区之类的功能。[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可为你实现这些接口。 相反，你可以使用 Visual Studio 提供的更为直观的类和设计器。 不过，只要你愿意，你仍然可以直接在 VSTO 外接程序中实现扩展性接口。  
  
 有关 Visual Studio 为这些功能提供的类和设计器的详细信息，请参阅[自定义任务窗格](../vsto/custom-task-panes.md)、[功能区设计器](../vsto/ribbon-designer.md)和[创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)。  
  
## 可在 VSTO 外接程序中实现的扩展性接口  
 下表列出了你可以实现的扩展性接口以及支持这些接口的应用程序。  
  
|接口|描述|应用程序|  
|--------|--------|----------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|实现此接口可自定义功能区 UI。 **Note:**  可以将“功能区 \(XML\)”项添加到项目，以便在 VSTO 外接程序中生成默认 <xref:Microsoft.Office.Core.IRibbonExtensibility> 实现。 有关更多信息，请参见[功能区 XML](../vsto/ribbon-xml.md)。|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> 项目<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|实现此接口可创建自定义任务窗格。|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|实现此接口可创建 Outlook 窗体区域。|Outlook|  
  
 Microsoft Office 还定义了其他一些扩展性接口，例如 <xref:Microsoft.Office.Core.IBlogExtensibility>、<xref:Microsoft.Office.Core.EncryptionProvider> 和 <xref:Microsoft.Office.Core.SignatureProvider>。 Visual Studio 不支持在使用 Office 项目模板创建的 VSTO 外接程序中实现这些接口。  
  
## 使用扩展性接口  
 要使用扩展性接口自定义 UI 功能，请在 VSTO 外接程序项目中实现相应的接口。 然后，重写 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法以返回实现该接口的类的实例。  
  
 有关演示如何在 Outlook 的 VSTO 外接程序中实现 <xref:Microsoft.Office.Core.IRibbonExtensibility>、<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> 和 <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> 接口的示例应用程序，请参阅 [Office 开发示例](../vsto/office-development-samples.md) 中的 UI 管理器示例。  
  
### 实现扩展性接口的示例  
 下面的代码示例演示用于创建自定义任务窗格的 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> 接口的简单实现。 此示例定义两个类：  
  
-   `TaskPaneHelper` 类实现 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> 以创建和显示自定义任务窗格。  
  
-   `TaskPaneUI` 类提供任务窗格的 UI。`TaskPaneUI` 类的属性使类对于 COM 可见，从而使 Microsoft Office 应用程序能够发现该类。 在此示例中，UI 是一个空 <xref:System.Windows.Forms.UserControl>，但你可以通过修改代码来添加控件。  
  
    > [!NOTE]  
    >  要向 COM 公开 `TaskPaneUI` 类，你必须同时为项目设置“为 COM 互操作注册”属性。  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#1)]  
  
 有关实现 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> 的详细信息，请参阅 Microsoft Office 文档中的[在 2007 Office System 中创建自定义任务窗格](http://msdn.microsoft.com/zh-cn/256313db-18cc-496c-a961-381ed9ca94be)（英文）。  
  
### 重写 RequestService 方法的示例  
 下面的代码示例演示如何重写 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法以从前面的代码示例中返回 `TaskPaneHelper` 类的实例。 它将检查 *serviceGuid* 参数的值以确定请求的是哪个接口，然后返回实现该接口的对象。  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#2)]  
  
## 请参阅  
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)   
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [从其他 Office 解决方案调用 VSTO 外接程序中的代码](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)  
  
  