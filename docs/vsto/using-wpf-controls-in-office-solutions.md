---
title: "在 Office 解决方案中使用 WPF 控件 | Microsoft Docs"
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
  - "WPF [Visual Studio 中的 Office 开发]"
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 在 Office 解决方案中使用 WPF 控件
  虽然使用 Visual Studio 中的 Office 开发工具创建的解决方案旨在直接使用 Windows 窗体控件，但你也可以在解决方案中使用 WPF 控件。  Windows Presentation Foundation \(WPF\) 就设计用户界面这方面而言可替代 Windows 窗体。  WPF 使用一种称为可扩展应用程序标记语言 \(XAML\) 的标记语言提供用于整合 UI、媒体和文档的新技术。  有关详细信息，请参阅 [Visual Studio 2015 中的 WPF 简介](../Topic/Introduction%20to%20WPF%20in%20Visual%20Studio%202015.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 任何可以承载 Office 解决方案中的 Windows 窗体控件的 UI 元素也可以承载 WPF 控件。  其中包括以下元素：  
  
-   文档级自定义项中的文档和工作表。  
  
-   文档级自定义项中的操作窗格。  
  
-   VSTO 外接程序中的自定义任务窗格。  
  
-   Outlook VSTO 外接程序中的窗体区域。  
  
## 在设计时将 WPF 控件添加到 Office 项目  
 不能直接将 WPF 控件添加到 Office 解决方案中的 UI 元素。  请转而将**“用户控件 \(WPF\)”**项添加到你的项目中，并将其用作 WPF 控件的设计图面。  然后，将 WPF 用户控件添加到项目中的 UI 元素。  
  
#### 若要将 WPF 控件添加到操作窗格、自定义任务窗格中或窗体区域  
  
1.  打开要向其中添加自定义任务窗格、操作窗格或窗体区域的项目。  
  
2.  将**“用户控件 \(WPF\)”**项添加到项目中。  
  
3.  从**“工具箱”**，将 WPF 控件添加到 WPF 用户控件设计图面。  
  
     默认情况下，当 WPF 用户控件设计器处于打开状态时，**“工具箱”**仅包含 WPF 控件。  
  
4.  生成项目。  
  
5.  将操作窗格、窗体区域或自定义任务窗格添加到你的项目：  
  
    -   对于窗体区域，将**“Outlook 窗体区域”**项添加到项目。  有关详细信息，请参阅[如何：向 Outlook 外接程序项目中添加窗体区域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
    -   对于操作窗格，将**“操作窗格控件”**或**“用户控件”**项添加到项目。  有关详细信息，请参阅[如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)和[如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
    -   对于自定义任务窗格，请将**“用户控件”**项添加到项目。  有关详细信息，请参阅[如何：向应用程序中添加自定义任务窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。  
  
6.  从**“工具箱”**的 *ProjectName***“WPF 用户控件”**选项卡，将 WPF 用户控件拖动到操作窗格、窗体区域或自定义任务窗格的设计器。  
  
     Visual Studio 将自动创建一个在 UI 元素上承载 WPF 用户控件 <xref:System.Windows.Forms.Integration.ElementHost> 的对象。  
  
7.  重新生成项目。  
  
#### 若要将 WPF 控件添加到文档或文档级项目中的工作表  
  
1.  打开 Word 或 Excel 文档级项目。  
  
2.  将**“用户控件 \(WPF\)”**项添加到项目中。  
  
3.  从**“工具箱”**，将 WPF 控件添加到 WPF 用户控件设计图面。  
  
4.  生成项目。  
  
5.  将**“用户控件”**项（即，Windows 窗体用户控件）添加到该项目。  
  
6.  打开 Windows 窗体用户控件的设计器。  
  
7.  从**“工具箱”**的 *ProjectName***“WPF 用户控件”**选项卡，将 WPF 用户控件拖动到该设计器中。  
  
     Visual Studio 将自动创建一个在 Windows 窗体用户控件中承载 WPF 用户控件 <xref:System.Windows.Forms.Integration.ElementHost> 的对象。  
  
8.  编写以编程方式将 Windows 窗体用户控件添加到文档或工作簿的代码。  有关详细信息，请参阅[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
    > [!NOTE]  
    >  不能将 Windows 窗体用户控件拖动到设计器中的文档或工作表中。  
  
9. 重新生成项目。  
  
## 使用 ElementHost 类承载 WPF 控件  
 Visual Studio 提供了有助于你在 Office 解决方案中使用 Windows 窗体控件的功能，但不提供针对 WPF 控件的类似功能。  例如，你可以在设计时通过从**“工具箱”**拖动控件或者在运行时通过使用帮助程序方法将 Windows 窗体控件添加到文档和工作表。  但是，这些工具不可用于 WPF 控件。  
  
 WPF 控件使用 <xref:System.Windows.Forms.Integration.ElementHost> 类，作为一个 Windows 窗体控件或窗体与 WPF 控件之间的集成层。  当在设计时将 WPF 控件添加到解决方案时，Visual Studio 会为你自动生成 <xref:System.Windows.Forms.Integration.ElementHost> 对象。  
  
## WPF 资源  
 有关用于在 Windows 窗体控件和窗体上承载 WPF 控件的体系结构和设计问题的详细信息，请参阅以下主题：  
  
-   [Windows 窗体和 WPF 互操作性输入体系结构](../Topic/Windows%20Forms%20and%20WPF%20Interoperability%20Input%20Architecture.md)  
  
-   [Windows 窗体和 WPF 属性映射](../Topic/Windows%20Forms%20and%20WPF%20Property%20Mapping.md)  
  
-   [WPF 和 Windows 窗体互操作](../Topic/WPF%20and%20Windows%20Forms%20Interoperation.md)  
  
-   [Windows 窗体控件和等效的 WPF 控件](../Topic/Windows%20Forms%20Controls%20and%20Equivalent%20WPF%20Controls.md)  
  
 有关在设计时将 WPF 控件添加到 Visual Studio 中 Windows 窗体控件和窗体的详细信息，请参阅以下主题：  
  
-   [演练：设计时在 Windows 窗体上创建新的 WPF 内容](../Topic/Walkthrough:%20Creating%20New%20WPF%20Content%20on%20Windows%20Forms%20at%20Design%20Time.md)  
  
-   [演练：设计时在 Windows 窗体上排列 WPF 内容](../Topic/Walkthrough:%20Arranging%20WPF%20Content%20on%20Windows%20Forms%20at%20Design%20Time.md)  
  
-   [演练：设置 WPF 内容的样式](../Topic/Walkthrough:%20Styling%20WPF%20Content.md)  
  
## 请参阅  
 [Office UI 自定义](../vsto/office-ui-customization.md)   
 [Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [自定义任务窗格](../vsto/custom-task-panes.md)   
 [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)   
 [如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何：向应用程序中添加自定义任务窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [如何：向 Outlook 外接程序项目中添加窗体区域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  