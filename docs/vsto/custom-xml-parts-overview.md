---
title: "自定义 XML 部件概述 |Microsoft 文档"
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
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5891cb7aa85012bbf99b1dd2e35b86ba3c263790
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="custom-xml-parts-overview"></a>Custom XML Parts Overview
  对于某些 Microsoft Office 应用程序，可在文档中嵌入 XML 数据。 时在文档中嵌入 XML 数据，数据被称为*自定义 XML 部件*。  
  
 可使用 Visual Studio 中的 VSTO 外接程序或文档级解决方案来创建和修改自定义 XML 部件。 无需启动 Microsoft Office 应用程序来创建和修改自定义 XML 部件。  
  
 **适用于：**本主题中的信息适用于文档级别项目和 VSTO 外接程序项目于 Excel、 PowerPoint 和 Word。 有关详细信息，请参阅 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
> [!NOTE]  
>  Visual Studio 还使你能够在文档级自定义项中缓存数据对象。 尽管有一些相似之处，此功能并不同于自定义 XML 部件。 有关详细信息，请参阅[文档级自定义项中缓存数据](../vsto/cached-data-in-document-level-customizations.md)。  
  
## <a name="understanding-custom-xml-parts"></a>了解自定义 XML 部件  
 自定义 XML 部件和 Open XML 格式一起在 2007 Microsoft Office 系统中引入。 这些格式包括 Excel、PowerPoint 和 Word 的新的基于 XML 的文件格式（如 .xlsx、.pptx 和 .docx）。 这些格式中的文档包含的 XML 文件 (也名为*XML 部件*) 整理在 ZIP 存档中的文件夹。 大多数 XML 部件为有助于定义文档的结构和状态的内置部件。 但文档还可包含自定义 XML 部件，可用于将任意 XML 数据存储在文档中。  
  
 XML 文件格式使应用程序能够以旧的二进制文件格式（如 .xls、.ppt 和 .doc）无法实现的方式来处理文档。 可读取 ZIP 存档的所有应用程序都可检查和修改文档内容，即使未安装 Microsoft Office。  
  
 有关 Open XML 和自定义 XML 部件的结构的详细信息，请参阅以下文章：  
  
-   [介绍 Office (2007) Open XML 文件格式](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [如何： 处理 Open XML 格式文档](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [演练： Word 2007 XML 格式](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [生成使用 Open XML 的 Word 2007 文档格式](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel、Word 和 PowerPoint 还使你可以使用以二进制文件格式保存的文档中的自定义 XML 部件。 但如果文档以二进制格式保存，则无法添加或修改自定义 XML 部件，除非启动 Microsoft Office 应用程序。  
  
## <a name="creating-and-modifying-custom-xml-parts"></a>创建和修改自定义 XML 部件  
 当文档在 Office 应用程序中打开时，或当文档关闭时，可创建或修改自定义 XML 部件，即使未安装 Microsoft Office。  
  
### <a name="modifying-xml-parts-while-the-office-application-is-running"></a>在 Office 应用程序正在运行时修改 XML 部件  
 通过使用文档级自定义项或 VSTO 外接程序，可使用自定义 XML 部件。 如果使用文档级自定义项，通常将使用自定义文档中的自定义 XML 部件。 如果使用 VSTO 外接程序，可创建或修改在应用程序中打开的任何文档中的自定义 XML 部件。  
  
 若要通过使用 Visual Studio 来创建自定义 XML 部件，请将新的 <xref:Microsoft.Office.Core.CustomXMLPart> 添加到文档中的 <xref:Microsoft.Office.Core.CustomXMLParts> 集合。 有关详细信息，请参阅下列主题：  
  
-   [如何：将自定义 XML 部件添加到文档级自定义项](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [如何：使用 VSTO 外接程序将自定义 XML 部件添加到文档](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modifying-xml-parts-without-starting-the-office-application"></a>在不启动 Office 应用程序的情况下修改 XML 部件  
 可在不启动 Excel、PowerPoint 或 Word 的情况下添加或修改自定义 XML 部件。 需在未安装 Microsoft Office 应用程序的计算机（如服务器）上使用文档中的 XML 数据时，这将非常有用。  
  
 若要在不启动 Microsoft Office 的情况下添加自定义 XML 部件，请使用 Open XML SDK 中的类。 这些类旨在提供对特定于 Office 文档的 Open XML 内容的访问。 例如，若要将自定义 XML 部件添加到 Excel 工作簿，你使用[AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a)方法[WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2)对象。 有关详细信息，请参阅[Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab)。  
  
## <a name="binding-custom-xml-parts-to-word-content-controls"></a>将自定义 XML 部件绑定到 Word 内容控件  
 可将 Word 解决方案中的内容控件绑定到自定义 XML 部件中的元素。 当内容控件绑定到自定义 XML 部件时，自定义 XML 部件中的数据将显示在内容控件的用户界面 (UI)。 如果用户编辑控件中的文本，则将自动更新相应的 XML 元素。 同样，如果自定义 XML 部件中的元素值发生更改，则绑定到 XML 元素的内容控件将显示新的数据。 有关详细信息，请参阅 [Content Controls](../vsto/content-controls.md)。  
  
## <a name="see-also"></a>另请参阅  
 [XML 架构和文档级自定义项中的数据](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [如何： 将自定义 XML 部件添加到文档级自定义项](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [如何： 使用 VSTO 外接程序将自定义 XML 部件添加到文档](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [内容控件](../vsto/content-controls.md)   
 [演练：将内容控件绑定到自定义 XML 部件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  