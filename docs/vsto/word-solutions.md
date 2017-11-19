---
title: "Word 解决方案 |Microsoft 文档"
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
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
ms.assetid: ef339ad8-1897-4a44-b588-e6004d0b6d8b
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b7fa4e3b548f5839b16a6bdeaf4a7d8ba6d00beb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="word-solutions"></a>Word 解决方案
  Visual Studio 提供可用于创建适用于 Microsoft Office Word 的文档级自定义项和 VSTO 外接程序的项目模板。 你可以使用这些解决方案来实现 Word 自动化、扩展 Word 功能以及自定义 Word 用户界面 (UI)。 有关文档级自定义项和 VSTO 外接程序之间的差异的详细信息，请参阅[Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  开发扩展的 Office 体验跨解决方案是否有兴趣[多个平台](https://dev.office.com/add-in-availability)？ 查看全新[Office 外接程序模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 外接程序具有内存占用较小与 VSTO 外接程序和解决方案，相比，并且你可以通过使用几乎任何 web 编程技术，例如 HTML5、 JavaScript、 CSS3 和 XML 生成它们。  
  
 本主题提供以下信息：  
  
-   [自动化 Word](#automating)。  
  
-   [开发 Word 的文档级自定义项](#doclevel)。  
  
-   [开发 Word 的 VSTO 外接程序](#applevel)。  
  
-   [自定义 Word 的用户界面](#UI)。  
  
##  <a name="automating"></a> 自动化 Word  
 Word 对象模型公开了许多可用于实现 Word 自动化的类型。 例如，可以通过编程方式创建表格、设置文档格式以及设置范围和段落中的文本。 有关详细信息，请参阅 [Word Object Model Overview](../vsto/word-object-model-overview.md)。  
  
 在 Visual Studio 中开发 Word 解决方案时，还可以使用解决方案中的 *主机项* 和 *主机控件* 。 这些对象可扩展 Word 对象模型中的某些常用对象，例如 <xref:Microsoft.Office.Interop.Word.Document> 和 <xref:Microsoft.Office.Interop.Word.ContentControl> 对象。 扩展对象的行为类似于其所基于的 Word 对象，但它们可以将其他事件和数据绑定功能添加到对象。 有关更多信息，请参见 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)。  
  
##  <a name="doclevel"></a> Developing Document-Level Customizations for Word  
 Microsoft Office Word 的文档级自定义项包含与特定文档相关联的程序集。 此程序集通常可通过自定义 UI 和自动化 Word 来扩展文档。 不同于与 Word 自身相关联的 VSTO 外接程序，在自定义中实现的功能只有当关联文档在 Word 中打开时才可用。  
  
 若要创建 Word 的文档级自定义项目，可使用 Visual Studio 的 **“新建项目”** 对话框中的“Word 文档”或“Word 模板”项目模板。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 若要深入了解文档级自定义项的工作原理，请参阅 [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md)。  
  
### <a name="word-customization-programming-model"></a>Word 自定义项编程模型  
 在创建 Word 的文档级项目时，Visual Studio 将生成一个名为 `ThisDocument`的类，这是解决方案的基础。 此类表示与解决方案相关联的文档，并提供用于编写代码的起点。  
  
 若要深入了解你可在文档级项目中使用的 `ThisDocument` 类和其他功能，请参阅 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)。  
  
##  <a name="applevel"></a> 开发 Word 的 VSTO 外接程序  
 Microsoft Office Word 的 VSTO 外接程序包含由 Word 加载的程序集。 此程序集通常可通过自定义 UI 和自动化 Word 来扩展 Word。 不同于与特定文档相关联的文档级自定义项，VSTO 外接程序中实现的功能不局限于任何单个文档。  
  
 若要创建 Word 的 VSTO 外接程序项目，可使用 Visual Studio 的 **“新建项目”** 对话框中的 Word 外接程序项目模板。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 有关 VSTO 外接程序工作原理的常规信息，请参阅 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。  
  
### <a name="word-add-in-programming-model"></a>Word 外接程序编程模型  
 在创建 Word VSTO 外接程序项目时，Visual Studio 将生成一个名为 `ThisAddIn`的类，这是解决方案的基础。 此类提供编写代码的起点，并且还对 VSTO 外接程序公开 Word 的对象模型。  
  
 若要深入了解你可在文档级项目中使用的 `ThisAddIn` 类和其他功能，请参阅 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
##  <a name="UI"></a> Customizing the User Interface of Word  
 可通过若干不同方式来自定义 Word 的用户界面。 某些选项适用于所有项目类型，而其他选项仅适用于 VSTO 外接程序或文档级自定义项。  
  
### <a name="options-for-all-project-types"></a>适用于所有项目类型的选项  
 下表列出了可用于文档级自定义项和 VSTO 外接程序的自定义选项。  
  
|任务|更多相关信息|  
|----------|--------------------------|  
|自定义功能区。|[功能区概述](../vsto/ribbon-overview.md)|  
|将 Windows 窗体控件或扩展的 Word 控件添加到（文档级自定义项的）自定义文档中，或添加到（VSTO 外接程序的）任何打开文档中。|[如何：将 Windows 窗体控件添加到 Office 文档](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [如何：将内容控件添加到 Word 文档](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [如何：将书签控件添加到 Word 文档](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>适用于文档级自定义项的选项  
 下表列出了仅适用于文档级自定义项的自定义选项。  
  
|任务|更多相关信息|  
|----------|--------------------------|  
|将操作窗格添加到文档。|[操作窗格概述](../vsto/actions-pane-overview.md)<br /><br /> [如何：将操作窗格添加到 Word 文档或 Excel 工作簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|将扩展的 XMLNode 和 XMLNodes 控件添加到文档图面中。|[如何：将 XMLNode 控件添加到 Word 文档](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [如何：将 XMLNodes 控件添加到 Word 文档](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>适用于 VSTO 外接程序的选项  
 下表列出了仅适用于 VSTO 外接程序的自定义选项。  
  
|任务|更多相关信息|  
|----------|--------------------------|  
|创建自定义任务窗格。|[自定义任务窗格](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>相关主题  
  
|标题|说明|  
|-----------|-----------------|  
|[Word Object Model Overview](../vsto/word-object-model-overview.md)|概述由 Word 对象模型提供的主类型。|  
|[Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)|提供有关可在 Word 解决方案中使用的扩展对象（由 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]提供）的信息。|  
|[Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)|介绍如何将 Windows 窗体控件添加到 Word 文档。|  
|[演练：创建你的第一个 Word 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|演示如何创建 Word 的基本文档级自定义项。|  
|[演练：创建你的第一个 Word VSTO 外接程序](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|演示如何创建 Word 的基本 VSTO 外接程序。|  
|[演练：运行时在 VSTO 外接程序中将控件添加到文档](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|演示如何使用 VSTO 外接程序在运行时将 Windows 窗体按钮和 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 添加到文档。|  
|[Office 开发中的 Word 2010](http://go.microsoft.com/fwlink/?LinkId=199020)|提供关于开发 Word 解决方案（不特定于使用 Visual Studio 的 Office 开发）的文章和参考文档的链接。|  
  
  