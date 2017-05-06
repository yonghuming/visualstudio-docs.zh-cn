---
title: "文档级自定义项中的 XML 架构和数据"
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
  - "Visual Studio 中的 Office 开发, XML"
  - "架构 [Visual Studio 中的 Office 开发]"
  - "XML [Visual Studio 中的 Office 开发], XML 架构"
  - "XML 架构 [Visual Studio 中的 Office 开发]"
  - "XML 架构 [Visual Studio 中的 Office 开发], 关于 XML 架构和数据"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 文档级自定义项中的 XML 架构和数据
  **重要事项** 有关 Microsoft Word 的本主题开头的信息对于位于美国境外及其领土或使用对单个的优点和使用完全呈现和组织，或者运行的开发的程序，即在 2010 年一月之前的 Microsoft 许可证的 Microsoft Word 产品，那么，当 Microsoft 从 Microsoft Word 移除了特殊功能的实现与自定义 XML 相关。  凡位于美国及其各州内的个体或组织，在使用或开发用于在由 Microsoft 于 2010 年 1 月 10 日之后授予许可的 Microsoft Word 产品上运行的程序时，请勿参考或使用此与 Microsoft Word 相关的信息；这些产品与此许可日期之前的产品，或在美国以外的国家\/地区销售和授予使用许可的产品的行为不同。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel 和 Microsoft Office Word 提供了用于将架构映射到文档的功能。  此功能可以简化在文档中导入和导出 XML 数据的操作。  
  
 Visual Studio 以编程模型中的控件的形式在文档级自定义项中公开映射的架构元素。  对于 Excel，Visual Studio 增加了将控件绑定到数据库、Web 服务及对象中的数据的支持。  Visual Studio 还为 Word 和 Excel 增加了对操作窗格的支持，可以将操作窗格与架构映射文档一起使用，为解决方案的最终用户带来更佳的体验。  有关更多信息，请参见[操作窗格概述](../vsto/actions-pane-overview.md)。  
  
> [!NOTE]  
>  不能在 Excel 解决方案中使用多部分 XML 架构。  
  
## 架构附加到 Excel 工作簿时创建的对象  
 将架构附加到在工作簿时，Visual Studio 将自动创建若干对象，并将它们添加到项目中。  由于这些对象由 Excel 进行管理，因此不应使用 Visual Studio 工具删除这些对象。  若要删除这些对象，请使用 Excel 工具将映射元素从工作表中移除或分离架构。  
  
 有两个主要对象：  
  
-   XML 架构（XSD 文件）。  对于工作簿中的每个架构，Visual Studio 都会向项目中添加一个架构。  该架构在**“解决方案资源管理器”**中显示为一个带 XSD 扩展名的项目项。  
  
-   类型化 <xref:System.Data.DataSet> 类。  此类是基于架构创建的。  此数据集类在**“类视图”**中可见。  
  
## 当架构元素映射到 Excel 工作表时创建的对象  
 将来自**“XML 源”**任务窗格的架构元素映射到工作表时，Visual Studio 会自动创建几个对象并将它们添加到项目中：  
  
-   控件。  对于工作簿中的每个映射对象，都会在编程模型中创建一个 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件（用于非重复架构元素）或 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件（用于重复架构元素）。  只有通过从工作簿中删除映射和映射对象，才能将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件删除。  有关控件的更多信息，请参见 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
-   BindingSource。  通过将非重复架构元素映射到工作表创建 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 时，会创建一个 <xref:System.Windows.Forms.BindingSource> 并将 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控件绑定到 <xref:System.Windows.Forms.BindingSource>。  必须将 <xref:System.Windows.Forms.BindingSource> 绑定到与映射到文档的架构匹配的数据源的实例，如创建的类型化 <xref:System.Data.DataSet> 类的实例。  通过设置**“属性”**窗口中公开的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 属性创建绑定。  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> 不是为 <xref:Microsoft.Office.Tools.Excel.ListObject> 对象创建的。  必须通过设置**“属性”**窗口中的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 属性将 <xref:Microsoft.Office.Tools.Excel.ListObject> 手动绑定到数据源。  
  
### Office 映射架构与 Visual Studio 数据源窗口  
 Office 的映射架构功能和 Visual Studio**“数据源”**窗口可以帮助您在 Excel 工作表上呈现数据，以用于报告或编辑。  在这两种情况下，都可以将数据元素拖到 Excel 工作表上。  这两种方法都会创建通过 <xref:System.Windows.Forms.BindingSource> 绑定到数据源（如 <xref:System.Data.DataSet> 或 Web 服务）的控件。  
  
> [!NOTE]  
>  当您将重复的架构元素映射到工作表时，Visual Studio 会创建一个 <xref:Microsoft.Office.Tools.Excel.ListObject>。  <xref:Microsoft.Office.Tools.Excel.ListObject> 不是通过 <xref:System.Windows.Forms.BindingSource> 自动绑定到数据的。  必须通过设置**“属性”**窗口中的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 属性将 <xref:Microsoft.Office.Tools.Excel.ListObject> 手动绑定到数据源。  
  
 下表显示了这两种方法之间的一些差异。  
  
|XML 架构|“数据源”窗口|  
|------------|-------------|  
|使用 Office 界面。|使用 Visual Studio 中的**“数据源”**窗口。|  
|启用内置 Office 功能，以便在 XML 文件中导入和导出数据。|必须以编程方式提供导入和导出功能。|  
|必须编写代码以使用数据填充生成的控件。|从**“数据源”**窗口添加的控件具有自动生成的填充控件的代码，使用数据库服务器时还会有必要的连接字符串。|  
  
## 架构附加到 Word 文档时的行为  
 将架构附加到在文档级 Office 项目中使用的 Word 文档时，并不会创建数据对象。  但是，将架构元素映射到文档时会创建控件。  控件的类型取决于所映射的元素的类型；重复元素生成 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件，非重复元素生成 <xref:Microsoft.Office.Tools.Word.XMLNode> 控件。  有关更多信息，请参见[XMLNodes 控件](../vsto/xmlnodes-control.md)和[XMLNode 控件](../vsto/xmlnode-control.md)。  
  
## 部署包含 XML 架构的解决方案  
 应该创建一个安装程序，以部署使用映射到文档的 XML 架构的解决方案。  该安装程序应该在用户计算机上的架构库中注册此架构。  如果没有注册此架构，解决方案也仍然能工作，因为 Word 会在用户打开文档时根据文档中的元素创建一个临时架构。  但是，用户将不能根据用于创建项目的架构进行验证或将此架构保存。  有关安装程序的更多信息，请参见 [部署应用程序、服务器和组件](../deployment/deploying-applications-services-and-components.md)。  
  
 也可以向项目添加代码，以检查架构是否位于库中，以及是否已经注册。  如果未在库中或未注册，可以向用户发出警告。  
  
 [!code-csharp[Trin_VstcoreDataWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstcoreDataWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/VB/ThisDocument.vb#1)]  
  
## 请参阅  
 [如何：将架构映射到 Visual Studio 内部的 Word 文档](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [如何：将架构映射到 Visual Studio 内部的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  