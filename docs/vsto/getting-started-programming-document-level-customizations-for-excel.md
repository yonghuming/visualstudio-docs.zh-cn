---
title: "入门文档级自定义项编程 Excel |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1755aa5c8e54bd1b84e0f88ea70b4163f3a87af6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Excel 文档级自定义项编程入门
  如果你刚开始使用 Visual Studio 创建 Microsoft Office Excel 文档级自定义项，下面是你需要知道。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>了解如何使用文档级自定义项的 Excel 工作  
 基于 Excel 的文档级自定义项的是单个工作簿。 若要开始使用自定义项，最终用户打开工作簿或 Excel 模板创建的工作簿。 工作簿，例如在单元格中键入或单击按钮和菜单项中的事件可以在程序集中调用事件处理方法。 当关闭工作簿时，提供自定义项的功能将不再在 Excel 中，仅在包含它们的文档中可用。  
  
 有关详细信息，请参阅[体系结构的文档级自定义](../vsto/architecture-of-document-level-customizations.md)。  
  
## <a name="creating-document-level-projects-for-excel"></a>为 Excel 创建文档级项目  
 若要创建 Excel 的文档级自定义项，使用中的 Excel 工作簿或 Excel 模板项目模板**新项目**对话框。 这些模板包括所需程序集引用和项目文件。  
  
 有关如何为 Excel 创建文档级项目的详细信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。 有关项目模板的详细信息，请参阅[Office 项目模板概述](../vsto/office-project-templates-overview.md)。  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>通过使用主机项和主机控件的编程 Excel 工作簿  
 *主机项*和*宿主控件*是提供用于使用 Visual Studio 创建的文档级自定义项编程模型的类。  
  
 主机项提供的入口点为你的代码，并且它们还可以充当主机控件和 Windows 窗体控件的容器。 在 Excel 的文档级项目，这些主机项表示通过`ThisWorkbook`， `Sheet1`， `Sheet2`，和`Sheet3`类。  
  
 主机控件基于本机 Excel 对象，例如列表对象和范围。 宿主控件提供了类似功能的本机 Excel 对象，但它们还具有新的事件、 设计器支持和数据绑定功能。 它们显示为在你的项目代码并在 IntelliSense 中，它可以轻松而无需导航 Excel 对象模型引用在代码中直接的特定对象的第一类对象。  
  
 有关详细信息，请参阅下列主题：  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>自定义 Excel 的用户界面  
 大多数 Microsoft Office 解决方案的 Office 应用程序提供用户与解决方案交互某种方式修改的用户界面 (UI)。 有多种方法使用的文档级自定义项可以在其中修改 Excel 的 UI。 例如，可以将控件添加到功能区中，也可以显示操作窗格。 有关详细信息，请参阅[Office UI 自定义项](../vsto/office-ui-customization.md)。  
  
 你也可以打开与你直接在 Visual Studio 中的项目相关联的工作簿。 在 Visual Studio 中打开工作簿时，你可以通过使用 Excel 用户界面来修改该工作簿。 你还可以作为设计界面，可用于将控件拖到工作表中使用工作簿。 有关详细信息，请参阅[Visual Studio 环境中的 Office 项目](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## <a name="using-data-binding"></a>使用数据绑定  
 主机控件也存在在可以将中的控件的列表中**数据源**窗口。 在此方式自动添加主机控件将将它们绑定到数据源，你将其设置使用窗口。 无需编写任何代码，可以显示来自数据库、 web 服务和业务对象数据。 有关详细信息，请参阅[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
## <a name="next-steps"></a>后续步骤  
 若要了解如何创建 Excel 的文档级自定义项，请参阅[演练： 创建你第一个文档级自定义 excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)。 本演练向你介绍 Visual Studio 和 Excel 文档级自定义项的编程模型中的 Office 开发工具。  
  
 有关指导你完成一些 Excel 项目中的常见任务的主题的列表，请参阅[Office 编程中的常见任务](../vsto/common-tasks-in-office-programming.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [文档级自定义项编程](../vsto/programming-document-level-customizations.md)   
 [Excel 解决方案](../vsto/excel-solutions.md)   
 [演练： 创建你的第一个文档级自定义 excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)   
 [Excel 对象模型概述](../vsto/excel-object-model-overview.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)  
  
  