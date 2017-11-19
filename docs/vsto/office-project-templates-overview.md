---
title: "Office 项目模板概述 |Microsoft 文档"
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
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
ms.assetid: 2f86546b-307f-48ea-b01c-5f5a242fce17
caps.latest.revision: "68"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6066e5adbe4519011f56a4d88ecfcc834eb7788c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="office-project-templates-overview"></a>Office 项目模板概述
  Visual Studio 中的 Microsoft Office 开发人员工具包括用于创建以下类型的 Office 解决方案的项目模板：  
  
-   [文档级自定义项](#DocLevel)  
  
-   [VSTO 外接程序](#AppLevel)  
  
 有关这些类型的 Office 解决方案的详细比较，请参阅[Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Office 项目模板位于 **“新建项目”** 对话框中，你可以从 **“Visual C#”** 和 **“Visual Basic”** 语言节点的 **“Office”** 节点下找到该对话框。 每个模板都使用目标应用程序的相应配置来生成项目，包括程序集引用和调试设置。  
  
 每个项目都提供了文件和代码，使你可以开始使用特定类型的解决方案。 每个项目的生成代码都包括启动和关闭事件处理程序。 可以向这些事件处理程序添加代码，以便在加载解决方案时对其进行初始化，并在卸载解决方案时对其进行清理。 有关详细信息，请参阅 [Office Projects in the Visual Studio Environment](../vsto/office-projects-in-the-visual-studio-environment.md) 和 [Events in Office Projects](../vsto/events-in-office-projects.md)。  
  
> [!NOTE]  
>  Office 开发工具随某些 Visual Studio 版本提供。 有关详细信息，请参阅 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)。  
  
##  <a name="DocLevel"></a> Document-Level Customizations  
 **“新建项目”** 对话框中的 **“Office”** 节点提供下列项目模板，可以使用这些模板开始创建 Word 和 Excel 的文档级自定义项：  
  
-   **Word 2013 和 2016 VSTO 文档**  
  
-   **Word 2013 和 2016 VSTO 模板**  
  
-   **Excel 2013 和 2016 VSTO 工作簿**  
  
-   **Excel 2013 和 2016 VSTO 模板**  
  
-   **Word 2010 VSTO 文档**  
  
-   **Word 2010 VSTO 模板**  
  
-   **Excel 2010 VSTO 工作簿**  
  
-   **Excel 2010 VSTO 模板**  
  
 Word 文档和 Excel 工作簿项目模板提供了代码，使你可以开始创建基于特定文档或工作簿的解决方案。 在这些类型的解决方案中，只有在 Word 或 Excel 中打开关联的文档时，代码才运行。  
  
 “Word 模板”和“Excel 模板”项目模板的工作方式与“Word 文档”和“Excel 工作簿”项目模板相同。 但是，用户可以使用“Word 模板”和“Excel 模板”项目模板轻松地为解决方案中的自定义模板创建新的本地文档或工作簿副本。 用户从模板创建的新文档中提供了你的解决方案中的功能。  
  
> [!NOTE]  
>  引用托管代码扩展的 Word 模板不能被用作全局 VSTO 外接程序。如果从 Word 的 Startup 目录加载模板，则不会调用该程序集。 有关详细信息，请参阅 [全局模板和 Excel 外接程序（.xla 文件）的限制](#Limitations)  
  
 有关这些项目类型的入门信息，请参阅下列主题：  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Word 解决方案](../vsto/word-solutions.md)  
  
-   [Excel 解决方案](../vsto/excel-solutions.md)  
  
-   [演练：创建你的第一个 Word 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [演练：创建你的第一个 Excel 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a> VSTO 外接程序  
 **“新建项目”** 对话框中的 **“Office/SharePoint”** 节点提供下列项目模板，可以使用这些模板开始创建 VSTO 外接程序。  
  
-   **Excel 2013 和 2016 VSTO 外接程序**  
  
-   **InfoPath 2013 VSTO 外接程序**  
  
-   **Outlook 2013 和 2016 VSTO 外接程序**  
  
-   **PowerPoint 2013 和 2016 外接程序**  
  
-   **Project 2013 和 2016 外接程序**  
  
-   **Visio 2013 和 2016 外接程序**  
  
-   **Word 2013 和 2016 外接程序**  
  
-   **Excel 2010 外接程序**  
  
-   **InfoPath 2010 外接程序**  
  
-   **Outlook 2010 外接程序**  
  
-   **PowerPoint 2010 外接程序**  
  
-   **Project 2010 外接程序**  
  
-   **Visio 2010 外接程序**  
  
-   **Word 2010 外接程序**  
  
 当创建基于这些项目模板之一的项目时，解决方案中的代码会在关联应用程序打开时运行。 与文档级项目不同，代码不与单个文档关联。  
  
 有关这些项目类型入门的详细信息，请参阅下列主题：  
  
-   [VSTO 外接程序编程入门](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
-   [演练：创建你的第一个 Excel VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [演练：创建你的第一个 Outlook VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [演练：创建你的第一个 PowerPoint VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [演练：创建你的第一个 Project VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [演练：创建你的第一个 Word VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## <a name="document-vs-template-solutions"></a>文档 vs。模板解决方案  
 在围绕 Word 文档或 Excel 工作簿设计解决方案时，必须确定将该文档提供给用户的最佳方式。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 某些情况下，你可能希望为每位用户提供一份文档副本。 在这种情况下，可以使用 Excel 或 Word 文档项目创建解决方案。  
  
 而在其他情况下，你可能希望在某个服务器上提供一个模板，以便用户可以打开该模板并保存本地副本作为文档。 在这种情况下，可以使用 Excel 或 Word 模板项目创建解决方案。  
  
## <a name="comparison"></a>比较  
 下表概述了文档和模板之间的区别。  
  
|文档|模板|  
|---------------|---------------|  
|用户可以打开并修改文档，除非该文档被设置为只读。 任何保存过的更改都保留在原文档中。|用户可以打开模板以创建一个本地副本作为新文档。 用户不能修改原模板，除非他们被授予某些特权。|  
|打开时，文档将引发 <xref:Microsoft.Office.Tools.Word.Document.Open> 事件。|打开时，模板将引发 <xref:Microsoft.Office.Tools.Word.Document.New> 事件。|  
  
##  <a name="Limitations"></a> 全局模板和 Excel 外接程序（.xla 文件）的限制  
 文档、工作簿和模板可能不会像全局模板或 Excel VSTO 外接程序（.xla 文件）那样正常工作。  
  
## <a name="word-templates"></a>Word 模板  
 当 Microsoft Office Word 模板具有托管代码扩展时，如果该模板作为全局模板附加或者从 Word 的 Startup 目录中加载，则不会调用项目程序集。 此外，文档不识别属于 Office 解决方案的模板的格式。  
  
## <a name="excel-add-ins-xla-files"></a>Excel 外接程序（.xla 文件）  
 没有用于创建 Excel VSTO 外接程序（.xla 文件）的 Office 项目。 可以将工作簿另存为 .xla 文件，但这不是一种受支持的操作，建议你不要这样做。 如果你保存的工作簿具有托管代码扩展作为**Microsoft Office Excel 外接程序 (\*.xla)**文件，你可以选择在**外接程序**对话框中，将应用于另一个工作簿。 某些情况下，你的代码将在应用 VSTO 外接程序后在目标工作簿中运行，但不支持这样使用 Office 解决方案。  
  
## <a name="see-also"></a>另请参阅  
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [如何： 在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [入门文档级自定义项编程 for Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [入门文档级自定义项编程 Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [VSTO 外接程序编程入门](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  