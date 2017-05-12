---
title: "如何：用数据库中的数据填充工作表"
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
  - "数据 [Visual Studio 中的 Office 开发], 添加到工作表"
  - "数据库 [Visual Studio 中的 Office 开发], 填充工作表"
  - "工作表 [Visual Studio 中的 Office 开发], 填充"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：用数据库中的数据填充工作表
  可以在文档级 Office 的访问数据的方式应在 Windows 中访问数据的窗体项目。  可以使用相同的工具和代码将数据传入您的解决方案，甚至可以使用 Windows 窗体控件来显示这些数据。  此外，还可以使用称为宿主控件的控件，这些控件是 Microsoft Office Excel 中经过增强，具备事件和数据绑定功能的本机对象。  有关更多信息，请参见[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 下面的示例演示如何使用设计器在文档级项目中添加数据绑定控件。  有关演示如何在运行时向应用程序级项目中添加数据绑定控件的示例，请参见[演练：VSTO 外接程序项目中的复杂数据绑定](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)。  
  
 ![链接到视频](../vsto/media/playvideo.png "链接到视频") 如需相关视频演示，请参见 [How Do I: Transfer Data Into an Excel Worksheet?](http://go.microsoft.com/fwlink/?LinkID=130277)（如何实现：将数据传输到 Excel 工作表？）以及 [How Do I: Consume Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)（如何实现：在 Excel 中使用数据库数据？）。  
  
## 在设计时向工作表中添加数据绑定控件  
  
#### 用数据库中的数据填充工作表  
  
1.  在 Visual Studio 中打开一个 Excel 文档级项目，让工作表在设计器中打开。  
  
2.  打开**“数据源”**窗口，为项目创建一个数据源。  有关更多信息，请参见[如何：连接到数据库中的数据](~/data-tools/how-to-connect-to-data-in-a-database.md)。  
  
3.  将所需的字段或表从**“数据源”**窗口拖到工作表中。  
  
 将在工作表上创建以下控件之一：  
  
-   如果拖动字段，则会在工作表上创建 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  有关更多信息，请参见[NamedRange 控件](../vsto/namedrange-control.md)。  
  
-   如果拖动表，则会在工作表上创建 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件。  有关更多信息，请参见[ListObject 控件](../vsto/listobject-control.md)。  
  
 通过在**“数据源”**窗口中选择表或字段，然后从下拉列表中选择其他控件，您可以添加其他控件。  
  
## 项目中的对象  
 除了控件外，还会将以下数据相关对象自动添加到项目中：  
  
-   一个类型化数据集，该数据集封装您在数据库中所连接到的数据表。  有关更多信息，请参见[在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
-   一个 <xref:System.Windows.Forms.BindingSource>，它将控件连接到类型化数据集。  有关更多信息，请参见[BindingSource 组件概述](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)。  
  
-   一个 TableAdapter，将类型化数据集连接到数据库。  有关更多信息，请参见[TableAdapter 概述](/visual-studio/data-tools/tableadapter-overview)。  
  
-   一个 TableAdapterManager，用于在数据集中协调表适配器以便实现分层更新。  有关更多信息，请参见[分层更新](../data-tools/hierarchical-update.md)和[TableAdapterManager 概述](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)。  
  
 运行项目时，控件将显示数据源中的第一条记录。  可以使用 <xref:System.Windows.Forms.BindingSource>，以使用户能够在记录之间滚动。  
  
#### 滚动记录  
  
-   使用 <xref:System.Windows.Forms.BindingSource> 方法，比如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。  
  
 有关如何向类型化数据集和数据库发送更新的信息，请参见[如何：使用宿主控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [如何：用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：用服务中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [如何：使用宿主控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [如何：我将数据传输到 Excel 工作表](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [如何：我在 Excel 中使用数据库数据？](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  