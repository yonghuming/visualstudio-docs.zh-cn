---
title: "XML 架构和文档级自定义项中的数据 |Microsoft 文档"
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
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d53a17484a350e361459f5c975ed3090779332bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>文档级自定义项中的 XML 架构和数据
  **重要**提出有关 Microsoft Word 本主题中的信息不提供的以独占方式适合的好处和使用个人和组织用户位于美国和其区域之外，或使用，或开发在运行的程序，在 2010 年 1 月，Microsoft 中删除的特定功能实现的时间之前已授权的 Microsoft 的 Microsoft Word 产品被与 Microsoft Word 自定义 XML。 有关 Microsoft Word 此信息不能读取或使用的个人或美国或其地区熟悉使用，或开发在 Microsoft Word 2010 年 1 月 10 日之后已授权的 Microsoft 的产品运行的程序中的组织;这些产品将无法与产品许可在该日期之前或购买并获得美国以外的使用许可相同。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel 和 Microsoft Office Word 提供的功能将架构映射到你的文档。 此功能可以简化导入和导出 XML 数据的操作文档。  
  
 Visual Studio 公开映射为控件的编程模型中的文档级自定义项中的架构元素。 对于 Excel，Visual Studio 将添加对将控件绑定到数据库、 Web 服务和对象中的数据的支持。 对于 Word 和 Excel，Visual Studio 将添加对操作窗格，可以使用与架构映射文档来创建你的解决方案的增强的最终用户体验的支持。 有关更多信息，请参见 [Actions Pane Overview](../vsto/actions-pane-overview.md)。  
  
> [!NOTE]  
>  不能在 Excel 解决方案中使用多部分的 XML 架构。  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>对象创建架构附加到 Excel 工作簿  
 当将架构附加到的工作簿时，Visual Studio 将自动创建几个对象，并将它们添加到你的项目。 这些对象不应删除使用 Visual Studio 工具，因为它们由 Excel 中进行管理。 若要删除这些对象，从工作表中删除映射的元素或通过使用 Excel 工具分离架构。  
  
 有两个主要对象：  
  
-   XML 架构 （XSD 文件）。 对于工作簿中的每个架构，Visual Studio 将架构添加到项目。 这显示为一个带中的 XSD 扩展项目项**解决方案资源管理器**。  
  
-   类型化 <xref:System.Data.DataSet> 类。 此类是根据架构创建的。 此数据集类是在中可见**类视图**。  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>对象创建时架构元素映射到 Excel 工作表  
 当你映射的架构元素**XML 源**到工作表，Visual Studio 的任务窗格中自动创建几个对象，并将它们添加到你的项目：  
  
-   控件。 为工作簿中每个映射对象<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>（对于非重复架构元素） 的控件或<xref:Microsoft.Office.Tools.Excel.ListObject>（用于重复架构元素） 的控件在编程模型中创建。 <xref:Microsoft.Office.Tools.Excel.ListObject>可以仅通过从工作簿中删除映射和映射的对象删除控件。 有关控件的详细信息，请参阅[主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
-   BindingSource。 当你创建<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>通过将非重复架构元素映射到工作表中，<xref:System.Windows.Forms.BindingSource>创建和<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控件绑定到<xref:System.Windows.Forms.BindingSource>。 必须将绑定<xref:System.Windows.Forms.BindingSource>到映射到文档，例如类型化的实例的架构匹配的数据源实例<xref:System.Data.DataSet>已创建的类。 通过设置创建绑定<xref:System.Windows.Forms.BindingSource.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>属性，都公开在**属性**窗口。  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource>不会为创建<xref:Microsoft.Office.Tools.Excel.ListObject>对象。 你必须手动将绑定<xref:Microsoft.Office.Tools.Excel.ListObject>到数据源通过设置<xref:System.Windows.Forms.BindingSource.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>中的属性**属性**窗口。  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office 映射架构和 Visual Studio 数据源窗口  
 Office 和 Visual Studio 的映射的架构功能**数据源**窗口可帮助你在要报告或编辑的 Excel 工作表上显示数据。 在这两种情况下，可以将数据元素拖动 Excel 工作表。 这两种方法创建控件的数据绑定通过<xref:System.Windows.Forms.BindingSource>到数据源，如<xref:System.Data.DataSet>或 Web 服务。  
  
> [!NOTE]  
>  当将重复架构元素映射到工作表时，Visual Studio 将创建<xref:Microsoft.Office.Tools.Excel.ListObject>。 <xref:Microsoft.Office.Tools.Excel.ListObject>未自动绑定到数据通过<xref:System.Windows.Forms.BindingSource>。 你必须手动将绑定<xref:Microsoft.Office.Tools.Excel.ListObject>到数据源通过设置<xref:System.Windows.Forms.BindingSource.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>中的属性**属性**窗口。  
  
 下表显示了一些这两种方法之间的差异。  
  
|XML 架构|“数据源”窗口|  
|----------------|-------------------------|  
|使用 Office 接口。|使用**数据源**Visual Studio 中的窗口。|  
|使导入和导出 XML 文件中的数据的内置 Office 功能。|必须提供导入和导出功能以编程方式。|  
|你必须编写代码以用数据填充生成的控件。|添加从控件**数据源**窗口具有自动生成进行填充，以及必要的连接字符串时使用数据库服务器的代码。|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>当架构附加到 Word 文档时的行为  
 将架构附加到文档级 Office 项目中使用的 Word 文档时，不会创建数据对象。 但是，当架构元素映射到您的文档时，创建控件。 控件的类型取决于哪种类型的元素映射;重复元素生成<xref:Microsoft.Office.Tools.Word.XMLNodes>控件和生成的非重复元素<xref:Microsoft.Office.Tools.Word.XMLNode>控件。 有关详细信息，请参阅[XMLNodes 控件](../vsto/xmlnodes-control.md)和[XMLNode 控件](../vsto/xmlnode-control.md)。  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>部署包括 XML 架构的解决方案  
 你应创建安装程序以部署使用 XML 架构映射到文档的解决方案。 安装程序应在用户的计算机上的架构库中注册架构。 如果你没有注册的架构，则解决方案将仍工作因为 Word 生成基于时用户将其打开的文档中元素的临时架构。 但是，用户将不能执行验证或保存用于创建项目的架构。 有关安装程序的详细信息，请参阅[部署应用程序、 服务和组件](/visualstudio/deployment/deploying-applications-services-and-components)。  
  
 此外可以将代码添加到项目中以检查架构是否已在库中和注册。 如果不是这样，你可以对用户进行警告。  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>另请参阅  
 [如何： 将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [如何：将架构映射到 Visual Studio 内部的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  