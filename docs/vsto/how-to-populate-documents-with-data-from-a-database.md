---
title: "如何： 用数据库中的数据填充文档 |Microsoft 文档"
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
- documents, populating with data
- data, adding to documents
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e528bb0ef732400639f8604cf471d7f54a89ae73
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>如何：用数据库中的数据填充文档
  可以用访问 Windows 窗体项目中的数据的相同方式来访问 Microsoft Office 文档级项目中的数据。 使用相同的工具和代码将数据从数据库引入解决方案，然后即可使用 Windows 窗体控件来显示该数据。  
  
 此外，还可以使用主机控件来显示数据。 主机控件是指 Microsoft Office Word 中借助事件和数据绑定容量进行增强的本地对象。 有关更多信息，请参见 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 下列示例演示了如何使用设计器在文档级项目中添加数据绑定控件。 有关如何在运行时在 VSTO 外接程序项目中添加数据绑定控件的示例，请参阅[演练： 简单的数据绑定，在 VSTO 外接程序项目](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[将数据绑定到 Word 2007 内容控件使用 Visual Studio Tools for the Office System (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785)。  
  
## <a name="adding-a-control-to-a-document-at-design-time"></a>在设计时向文档添加控件  
  
#### <a name="to-populate-a-document-with-data-from-a-database"></a>使用数据库的数据填充文档  
  
1.  当文档在设计器中打开时，打开 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中 Word 文档级项目。  
  
2.  打开**数据源**窗口并从数据库创建数据源。 有关详细信息，请参阅[添加新连接](../data-tools/add-new-connections.md)。  
  
3.  将你想从的字段拖动**数据源**到您的文档窗口。  
  
 将内容控件添加到了该文档。 内容控件的类型取决于所选字段的数据类型。 有关详细信息，请参阅 [Content Controls](../vsto/content-controls.md)。  
  
 你可以通过选择中的数据字段添加一个不同的控件**数据源**窗口，然后从下拉列表中选择一个不同的控件。  
  
## <a name="objects-in-the-project"></a>项目中的对象  
 除了该控件，还会自动将以下数据相关的对象添加到你的项目：  
  
-   一个类型化数据集，它会封装数据库中你连接到的数据表。 有关详细信息，请参阅[Visual Studio 中的数据集工具](/visualstudio/data-tools/dataset-tools-in-visual-studio)。  
  
-   一个 <xref:System.Windows.Forms.BindingSource>，它将控件连接到类型化数据集。 有关详细信息，请参阅 [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview)。  
  
-   连接到数据库的类型化数据集的 TableAdapter。 有关详细信息，请参阅[创建和配置 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
-   TableAdapterManager，用于协调数据集中的表适配器来启用分层更新。 有关详细信息，请参阅[分层更新](../data-tools/hierarchical-update.md)和[TableAdapterManager 引用](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)。  
  
 运行项目时，该控件将显示数据源中的第一条记录。 可以借助 <xref:System.Windows.Forms.BindingSource> 来使用户能滚动显示各个记录。  
  
#### <a name="to-scroll-through-the-records"></a>滚动显示记录  
  
-   使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。  
  
 有关如何将更新发送到类型化数据集和数据库的信息，请参阅[如何： 使用主机控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## <a name="see-also"></a>另请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [添加新数据源](/visualstudio/data-tools/add-new-data-sources)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [如何： 用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何： 使用主机控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [使用 Office 解决方案概述中的本地数据库文件](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [连接到 Windows 窗体应用程序中的数据](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 组件概述](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  