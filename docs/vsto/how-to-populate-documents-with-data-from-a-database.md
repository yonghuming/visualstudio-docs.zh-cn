---
title: "如何：用数据库中的数据填充文档"
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
  - "数据, 添加到文档"
  - "文档, 用数据填充"
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：用数据库中的数据填充文档
  可以用访问 Windows 窗体项目中的数据的相同方式来访问 Microsoft Office 文档级项目中的数据。  使用相同的工具和代码将数据从数据库引入解决方案，然后即可使用 Windows 窗体控件来显示该数据。  
  
 此外，还可以使用主机控件来显示数据。  主机控件是指 Microsoft Office Word 中借助事件和数据绑定容量进行增强的本地对象。  有关详细信息，请参阅[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 下列示例演示了如何使用设计器在文档级项目中添加数据绑定控件。  有关如何在运行时在 VSTO 外接程序项目中添加数据绑定控件的示例，请参阅[演练：VSTO 外接程序项目中的简单数据绑定](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。  
  
 ![链接到视频](~/data-tools/media/playvideo.gif "链接到视频") 相关的视频演示，请参阅[使用 Visual Studio Tools for the Office System \(3.0\) 将数据绑定到 Word 2007 内容控件](http://go.microsoft.com/fwlink/?LinkId=136785)。  
  
## 在设计时向文档添加控件  
  
#### 使用数据库的数据填充文档  
  
1.  当文档在设计器中打开时，打开 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中 Word 文档级项目。  
  
2.  打开**“数据源”**窗口并从数据库创建数据源。  有关详细信息，请参阅[如何：连接到数据库中的数据](~/data-tools/how-to-connect-to-data-in-a-database.md)。  
  
3.  将所需字段从**“数据源”**窗口拖动到你的文档。  
  
 将内容控件添加到了该文档。  内容控件的类型取决于所选字段的数据类型。  有关详细信息，请参阅[内容控件](../vsto/content-controls.md)。  
  
 可通过以下方式来添加不同的控件：选择**“数据源”**窗口中的数据字段，然后从下拉列表中选择一个不同的控件。  
  
## 项目中的对象  
 除了该控件，还会自动将以下数据相关的对象添加到你的项目：  
  
-   一个类型化数据集，它会封装数据库中你连接到的数据表。  有关详细信息，请参阅 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
-   一个 <xref:System.Windows.Forms.BindingSource>，它将控件连接到类型化数据集。  有关详细信息，请参阅 [BindingSource 组件概述](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)。  
  
-   一个 TableAdapter，它将类型化数据集连接到数据库。  有关详细信息，请参阅 [TableAdapter 概述](/visual-studio/data-tools/tableadapter-overview)。  
  
-   一个 TableAdapterManager，它用于协调数据集中的表适配器来启用分层更新。  有关详细信息，请参阅[分层更新](../data-tools/hierarchical-update.md)和 [TableAdapterManager 概述](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)。  
  
 运行项目时，该控件将显示数据源中的第一条记录。  可以借助 <xref:System.Windows.Forms.BindingSource> 来使用户能滚动显示各个记录。  
  
#### 滚动显示记录  
  
-   使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。  
  
 有关如何将更新发送到类型化数据集和数据库的信息，请参阅[如何：使用宿主控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [如何：用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：使用宿主控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [在 Office 解决方案中使用本地数据库文件概述](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [连接到 Windows 窗体应用程序中的数据](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 组件概述](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  