---
title: "如何： 用服务中的数据填充文档 |Microsoft 文档"
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
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd71e73d205fb79199cb2b8847a856c97272b066
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-documents-with-data-from-services"></a>如何：用服务中的数据填充文档
  访问 Microsoft Office 文档级项目中的数据与访问 Windows 窗体项目中的数据的方式相同。 使用相同的工具和代码将数据引入解决方案，然后即可使用 Windows 窗体控件来显示该数据。 此外，可以利用称为“宿主控件”的控件，该控件是指 Microsoft Office Excel 和 Microsoft Office Word 中借助事件和数据绑定容量进行增强的本地对象。 有关详细信息，请参阅 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 下列示例演示了如何在设计时向文档中添加数据绑定控件。 有关如何在运行时在 VSTO 外接程序中添加数据绑定控件的示例，请参阅[演练： 绑定到数据服务中的 VSTO 外接程序项目](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md)。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[我如何交互与 Web 服务从 Microsoft Excel？](http://go.microsoft.com/fwlink/?LinkID=130284)。  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>使用 Web 服务的数据填充文档级项目  
  
1.  打开“数据源”  窗口并为项目创建服务数据源。 有关详细信息，请参阅[添加新数据源](/visualstudio/data-tools/add-new-data-sources)。  
  
2.  将所需的表或字段从“数据源”  窗口拖动到你的文档。  
  
     在文档中创建控件，创建绑定到项目中的对象类的 <xref:System.Windows.Forms.BindingSource> ，并为该服务生成类。  
  
3.  在代码中，创建在第 1 步中连接的 Web 服务类的实例。  
  
4.  如果与 Web 服务通信必须具有某些属性，则创建这些属性的实例。  
  
5.  使用 Web 服务公开的方法和第 4 步中创建的任何属性实例创建并发送数据请求。  
  
     使用的方法取决于 Web 服务提供的方法。  
  
6.  从 Web 服务向 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 的 <xref:System.Windows.Forms.BindingSource>属性分配数据响应。  
  
 运行项目时，控件显示数据源中的第一条记录。 可以通过使用 <xref:System.Windows.Forms.BindingSource>中的对象处理货币事件，从而滚动记录。  
  
## <a name="see-also"></a>另请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [添加新数据源](/visualstudio/data-tools/add-new-data-sources)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [如何： 用数据库中的数据填充工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何： 用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何： 用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：使用主机控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  