---
title: "文档级自定义项中的缓存数据"
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
  - "缓存数据 [Visual Studio 中的 Office 开发], 关于缓存数据"
  - "数据 [Visual Studio 中的 Office 开发], 缓存"
  - "数据 [Visual Studio 中的 Office 开发], 文档级解决方案"
  - "数据缓存 [Visual Studio 中的 Office 开发], 关于数据缓存"
  - "数据岛 [Visual Studio 中的 Office 开发]"
  - "文档级自定义项 [Visual Studio 中的 Office 开发], 数据模型"
  - "视图 [Visual Studio 中的 Office 开发]"
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 文档级自定义项中的缓存数据
  文档级自定义项的主要目标是将 Office 文档中的数据与视图分开。  数据是指存储在文档中的信息，包括数字和文本。  视图是指 Microsoft Office Word 和 Microsoft Office Excel 的用户界面和对象模型。  
  
 Visual Studio 通过实现以“数据岛”（也称为“数据缓存”）形式嵌入数据，从而将文档级自定义项中的数据与视图分开。  无需启动 Word 或 Excel 便可直接读取或修改数据。  如果需要在未安装 Microsoft Office 的服务器上的文档中修改数据，此方法非常有用。  Word 和 Excel 的设计初衷是在客户端环境中使用；而非在服务器上运行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有关文档级自定义项的更多信息，请参见 [Office 解决方案开发概述 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)和[文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)。  
  
## 了解缓存数据编程模型  
 数据岛可以包含满足某些要求的解决方案中的任何对象。  这些对象包括 <xref:System.Data.DataSet> 对象﹑<xref:System.Data.DataTable> 对象以及可由 <xref:System.Xml.Serialization.XmlSerializer> 类序列化的任何其他对象。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。  
  
 若要提供缓存数据的视图，可将文档上的 Windows 窗体控件和“宿主控件”绑定到数据岛中的对象上。  数据岛与数据绑定控件之间的数据绑定将使二者保持同步。  也可以将验证代码添加到独立于控件的数据中。  有关更多信息，请参见[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 宿主控件是 Excel 和 Word 对象模型中本机对象的扩展版本。  与本机对象不同的是，宿主控件可以直接绑定到托管数据对象上。  有关更多信息，请参见[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)和[Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
## 访问服务器上的缓存数据  
 若要访问文档中的缓存数据，可以使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类。  此类是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的一部分，不用运行 Excel 或 Word 便可在服务器上使用此类。  用户在您修改缓存数据后打开文档时，任何绑定到该数据的控件将自动与更改同步，并向用户呈现已更新的数据。  有关更多信息，请参见[访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 向服务器上的数据写入时不需要 Excel 和 Word，仅在客户端上查看数据时需要它们。  Excel 和 Word 甚至不需要安装在服务器上。  这提供了更好的可伸缩性，并且能够对包含数据岛的文档执行快速的批处理操作。  
  
## 缓存数据以便脱机使用  
 将数据存储在数据岛中可以支持脱机方案。  当用户最初从服务器上打开文档或请求文档时，数据岛将由最新的数据填充。  数据岛缓存在文档中，然后可以脱机使用。  这样，即使当时没有可用的连接，用户（及您的代码）也可以处理数据。  当用户重新连接时，可以将对数据所做的更改传回服务器数据源。  
  
## 比较缓存数据与自定义 XML 部件  
 自定义 XML 部件作为一种存储文档中的任意 XML 片段的方法引入到了 2007 Microsoft Office system 中。  尽管在许多情况下既可以使用自定义 XML 部件，也可以使用数据缓存，但数据岛与自定义 XML 部件之间存在一些差异。  有关自定义 XML 部件的更多信息，请参见[自定义 XML 部件概述](../vsto/custom-xml-parts-overview.md)。  
  
 下表列出了一些差异和相似性。  
  
||数据缓存|自定义 XML 部件|  
|-|----------|----------------|  
|哪些 Office 应用程序可以使用它们？|以下应用程序的文档级自定义项：<br /><br /> -   Excel<br />-   Word|以下应用程序的文档级和应用程序级解决方案：<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|可以存储哪些类型的数据？|满足某些要求的自定义项程序集中的任何公共对象。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。|任何 XML 数据。|  
|是否能够在不启动 Microsoft Office 应用程序的情况下访问数据？|是的，方法是通过使用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]提供的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类。|是的，方法是使用 <xref:System.IO.Packaging> 命名空间中的类，或者使用 Open XML 格式 SDK。|  
  
## 请参阅  
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [Visual Studio 中 Office 解决方案的体系结构](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  