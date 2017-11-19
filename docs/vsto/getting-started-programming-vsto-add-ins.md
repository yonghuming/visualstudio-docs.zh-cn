---
title: "入门 VSTO 外接程序编程 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 932827db3c12c3376dd74605c55e1bfed3c3e978
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-programming-vsto-add-ins"></a>Getting Started Programming VSTO Add-ins
  你可以使用 VSTO 外接程序来实现 Microsoft Office 应用程序自动化、扩展应用程序的功能，以及自定义应用程序的用户界面 (UI)。 可以通过使用 Visual Studio 创建 VSTO 外接程序如何与其他类型的 Office 解决方案进行比较有关信息，请参阅[Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="creating-vsto-add-in-projects"></a>创建 VSTO 外接程序项目  
 通过使用 VSTO 外接程序项目中的模板之一创建 VSTO 外接程序项目**新项目**对话框。 这些模板包括所需程序集引用和项目文件。 Visual Studio 为 Office 中的大多数应用程序提供 VSTO 外接程序项目模板。  
  
 有关如何创建 VSTO 外接程序项目的详细信息，请参阅[如何： 创建 Visual Studio 中的 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。 有关项目模板的详细信息，请参阅[Office 项目模板概述](../vsto/office-project-templates-overview.md)。  
  
## <a name="developing-vsto-add-in-projects"></a>开发 VSTO 外接程序项目  
 当你创建的 VSTO 外接程序项目时，Visual Studio 将自动创建 ThisAddIn.vb (在[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) 或 ThisAddIn.cs （在 C# 中) 代码文件。 此文件包含`ThisAddIn`类，该类为 VSTO 外接程序中提供了基础。 在加载或卸载 VSTO 外接程序时，可以使用此类的成员运行代码，以访问主机应用程序的对象模型，以及扩展应用程序的功能。 有关更多信息，请参见 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
## <a name="automating-applications-by-using-the-object-models"></a>使用对象模型实现应用程序自动化  
 Microsoft Office 应用程序的对象模型公开许多类型，可在 VSTO 外接程序中依据这些类型进行编程。 可以使用这些类型来实现应用程序自动化。 例如，可以通过编程方式在 Outlook 中创建和发送电子邮件，也可以在 Word 中打开文档和添加内容。 有关如何访问主机应用程序代码中的对象模型的详细信息，请参阅[VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。  
  
 有关特定 Microsoft Office 应用程序的对象模型的详细信息，请参阅以下主题：  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath 解决方案](../vsto/infopath-solutions.md)  
  
-   [PowerPoint 解决方案](../vsto/powerpoint-solutions.md)  
  
-   [Project 解决方案](../vsto/project-solutions.md)  
  
-   [Visio 对象模型概述](../vsto/visio-object-model-overview.md)  
  
## <a name="customizing-the-user-interface-of-applications"></a>自定义应用程序的用户界面  
 通过使用 VSTO 外接程序，可采用多种方式来自定义主机应用程序的 UI：  
  
-   对于 Excel 和 Word，可以向文档中添加托管控件。 有关详细信息，请参阅 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
-   如果应用程序支持功能区，则你可以自定义它。 有关详细信息，请参阅[功能区概述](../vsto/ribbon-overview.md)。  
  
-   如果应用程序支持自定义任务窗格，则你可以创建它。 有关详细信息，请参阅[自定义任务窗格](../vsto/custom-task-panes.md)。  
  
-   对于 Outlook，你可以创建自定义窗体区域。 有关更多信息，请参见 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)。  
  
-   对于所有 Microsoft Office 应用程序，可以在 VSTO 外接程序中显示 Windows 窗体。  
  
 有关如何自定义 UI 的 Microsoft Office 应用程序的详细信息，请参阅[Office UI 自定义项](../vsto/office-ui-customization.md)。  
  
## <a name="next-steps"></a>后续步骤  
 若要了解如何创建 VSTO 外接程序，请参阅下面的演练：  
  
-   [演练：创建你的第一个 Excel VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [演练：创建你的第一个 Outlook VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [演练：创建你的第一个 PowerPoint VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [演练：创建你的第一个 Project VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [演练：创建你的第一个 Word VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 这些演练介绍 Visual Studio 中的 Office开发工具和 VSTO 外接程序的编程模型。  
  
 有关指导你完成一些 Office 项目中的常见任务的主题的列表，请参阅[Office 编程中的常见任务](../vsto/common-tasks-in-office-programming.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [入门 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/getting-started-office-development-in-visual-studio.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  