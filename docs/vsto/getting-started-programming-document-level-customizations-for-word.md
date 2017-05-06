---
title: "Word 文档级自定义项编程入门"
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
  - "Word 项目 [Visual Studio 中的 Office 开发], 入门"
  - "Visual Studio 中的 Word 解决方案"
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Word 文档级自定义项编程入门
  如果您开始创建 Microsoft Office Word 的文档级自定义项使用 Visual Studio，则需要了解。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## 了解 Word 文档级自定义项的工作原理  
 创建的每个 Word 自定义项都基于单个文档。  要开始使用自定义项，最终用户需打开文档或者基于 Word 模板创建文档。  文档中的事件（例如将光标移入特定区域，或单击按钮和菜单项）可以调用程序集中的事件处理方法。  关闭文档后，自定义项提供的功能在 Word 中将不再可用。  
  
 有关更多信息，请参见[文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)。  
  
## 为 Word 创建文档级项目  
 若要为 Word 创建文档级自定义项，请使用**“新建项目”**对话框中的“Word 文档”或“Word 模板”项目模板。  这些模板包括所需程序集引用和项目文件。  
  
 有关如何为 Word 创建文档级项目的更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  有关项目模板的更多信息，请参见 [Office 项目模板概述](../vsto/office-project-templates-overview.md)。  
  
## 使用宿主项宿主控件对 Word 文档编程  
 “宿主项”和“宿主控件”是为文档级自定义项提供编程模型的类。  
  
 宿主项为代码提供入口点，并且，还可充当宿主控件和 Windows 窗体控件的容器。  在 Word 的文档级项目中，宿主项由 `ThisDocument` 类表示。  
  
 宿主控件基于本机 Word 对象，比如内容控件、书签和 XML 节点。  宿主控件提供与本机 Word 对象类似的功能，但它们还具有新的事件、设计器支持和数据绑定功能。  它们在项目代码和 IntelliSense 中作为第一类对象出现，从而可以更轻松地在您的代码中直接引用特定对象，而无需定位 Word 对象模型。  
  
 有关更多信息，请参见下列主题：  
  
-   [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)  
  
-   [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
## 自定义 Word 的用户界面  
 大多数 Microsoft Office 解决方案都会修改 Office 应用程序的用户界面 \(UI\)，以提供某种方式供用户与解决方案交互。  使用文档级自定义项，可通过多种方式来修改 Word 的 UI。  例如，您可以将控件添加到功能区，因此，您可以显示操作窗格。  有关更多信息，请参见[Office UI 自定义](../vsto/office-ui-customization.md)。  
  
 您也可以直接在 Visual Studio 中打开与项目关联的文档。  当文档在 Visual Studio 中打开时，可以使用 Word 用户界面修改文档。  还可以将文档用作设计图面，这使您能够将控件拖动到设计图面上。  有关更多信息，请参见[Visual Studio 环境中的 Office 项目](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## 将控件绑定到数据  
 内容控件和 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件位于可从**“数据源”**窗口中拖出的控件的列表中。  以这种方式添加内容控件和书签会将它们自动绑定到您使用该窗口设置的数据源。  无需编写任何代码，您就能够显示来自数据库、服务和业务对象的数据。  有关更多信息，请参见[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## 后续步骤  
 若要了解如何为 Word 创建文档级自定义项，请参见[演练：创建您的第一个 Word 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)。  本演练介绍 Visual Studio 中的 Office 开发工具以及 Word 文档级自定义项的编程模型。  
  
 有关指导您完成 Word 项目中的一些常规任务的主题列表，请参见 [Office 编程中的常规任务](../vsto/common-tasks-in-office-programming.md)。  
  
## 请参阅  
 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)   
 [Word 解决方案](../vsto/word-solutions.md)   
 [演练：创建您的第一个 Word 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)  
  
  