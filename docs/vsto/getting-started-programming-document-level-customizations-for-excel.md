---
title: "Excel 文档级自定义项编程入门 | Microsoft Docs"
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
  - "Excel 项目 [Visual Studio 中的 Office 开发], 入门"
  - "Visual Studio 中的 Excel 解决方案"
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Excel 文档级自定义项编程入门
  如果您开始创建 Microsoft Office Excel 的文档级自定义项使用 Visual Studio，则需要了解。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## 了解 Excel 的文档级自定义项的工作原理  
 Excel 的文档级自定义项基于单个工作簿。  若要开始使用自定义项，最终用户需打开工作簿或从 Excel 模板创建工作簿。  工作簿中的事件（例如在单元格中键入或单击按钮和菜单项）可以调用程序集中的事件处理方法。  当工作簿关闭时，自定义项提供的功能不再可用在 Excel 中，仅在包含其文档。  
  
 有关更多信息，请参见[文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)。  
  
## 创建 Excel 文档级项目  
 若要创建 Excel 文档级自定义项，请使用**“新建项目”**对话框中的“Excel 工作簿”或“Excel 模板”项目模板。  这些模板包括所需程序集引用和项目文件。  
  
 有关如何创建 Excel 文档级项目的更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  有关项目模板的更多信息，请参见 [Office 项目模板概述](../vsto/office-project-templates-overview.md)。  
  
## 使用宿主项和宿主控件对 Excel 工作簿进行编程  
 *宿主项* 和 *宿主控件*是对于文档级自定义项提供编程模型中创建 Visual Studio 中使用选件类。  
  
 宿主项为代码提供入口点，并且，还可充当宿主控件和 Windows 窗体控件的容器。  在 Excel 的文档级项目中，这些宿主项由 `ThisWorkbook`、`Sheet1`、`Sheet2` 和 `Sheet3` 类表示。  
  
 宿主控件基于本机 Excel 对象，如列表对象和范围。  宿主控件提供与本机 Excel 对象类似的功能，但它们还具有新的事件、设计器支持和数据绑定功能。  它们在项目代码和 IntelliSense 中作为一类对象出现，从而可以更轻松地在代码中直接引用特定对象，而无需定位 Excel 对象模型。  
  
 有关更多信息，请参见下列主题：  
  
-   [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)  
  
-   [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
## 自定义 Excel 的用户界面  
 大多数 Microsoft Office 解决方案都会修改 Office 应用程序的用户界面 \(UI\)，以提供某种方式供用户与解决方案交互。  使用文档级自定义项，可通过多种方式来修改 Excel 的 UI。  例如，您可以将控件添加到功能区，也可以显示操作窗格。  有关更多信息，请参见[Office UI 自定义](../vsto/office-ui-customization.md)。  
  
 您也可以直接在 Visual Studio 中打开与项目关联的工作簿。  当在 Visual Studio 中打开工作簿后，可以使用 Excel 用户界面修改工作簿。  还可以将工作簿用作设计图面，这使您能够向工作表上拖动控件。  有关更多信息，请参见[Visual Studio 环境中的 Office 项目](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## 使用数据绑定  
 宿主控件还出现在可从**“数据源”**窗口拖动的控件列表中。  以这种方式添加宿主控件将自动把它们绑定到您使用该窗口设置的数据源上。  无需编写任何代码，您就能够显示来自数据库、web 服务和业务对象的数据。  有关更多信息，请参见[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## 后续步骤  
 若要了解如何创建 Excel 的文档级自定义项，请参见[演练：创建您的第一个 Excel 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)。  此演练介绍 Visual Studio 中的 Office 开发工具以及 Excel 文档级自定义项的编程模型。  
  
 有关指导您完成 Excel 项目中的一些常见任务的主题列表，请参见 [Office 编程中的常规任务](../vsto/common-tasks-in-office-programming.md)。  
  
## 请参阅  
 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)   
 [Excel 解决方案](../vsto/excel-solutions.md)   
 [演练：创建您的第一个 Excel 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)   
 [Excel 对象模型概述](../vsto/excel-object-model-overview.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)  
  
  