---
title: "在 Visual Studio 中将控件绑定到数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "“数据源”窗口"
  - "数据源, 显示数据"
  - "数据, 显示"
  - "显示数据"
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual Studio 中将控件绑定到数据
通过将数据绑定到控件，可以向应用程序的用户显示数据。  可以通过将项从**“数据源”**窗口拖到 Visual Studio 的设计图面上来创建这些数据绑定控件。  
  
 本主题描述可用于创建数据绑定控件的数据源。  它还描述了数据绑定中涉及的一些常规任务。  有关如何创建数据绑定控件的详细细节，请参见[在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)、[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)和[在 Visual Studio 中将 Silverlight 控件绑定到数据](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)。  
  
## 数据源  
 数据源表示可用于应用程序的数据。  你可以从数据库、服务或对象创建数据源。  有关更多信息，请参见[数据源概述](../data-tools/add-new-data-sources.md)。  
  
 某些数据源支持你通过从**“数据源”**窗口拖动项来创建数据绑定控件，而其他数据源则不能。  下表显示了支持的数据源。  
  
|数据源|**Windows 窗体设计器**中的拖放支持|**WPF 设计器**中的拖放支持|**Silverlight 设计器**中的拖放支持|  
|---------|-----------------------------|-----------------------|-------------------------------|  
|数据集|是|是|否|  
|实体数据模型|不支持<sup>1</sup>|是|是|  
|LINQ to SQL 类|不支持<sup>2</sup>|不支持<sup>2</sup>|不支持<sup>2</sup>|  
|服务（包括 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]、WCF 服务和 Web 服务）|是|是|是|  
|对象|是|是|是|  
|SharePoint|是|是|是|  
  
 1.  当 Windows 窗体设计器处于打开状态时，**“数据源”**窗口中的实体为只读，并且无法拖到设计器。  不过，你仍然能够通过添加基于实体数据模型的新对象数据源，然后将这些对象拖到设计器来创建数据绑定控件。  
  
 2.  LINQ to SQL 类不会出现在**“数据源”**窗口中。  不过，你可以添加基于 LINQ to SQL 类的新对象数据源，然后将这些对象拖到设计器来创建数据绑定控件。  有关更多信息，请参见[演练：创建 LINQ to SQL 类（O\/R 设计器）](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)。  
  
## “数据源”窗口  
 数据源以**“数据源”**窗口中的项的形式提供给项目。  你可以从此窗口拖动项来创建绑定到基础数据的控件。  有关更多信息，请参见[“数据源”窗口](../Topic/Data%20Sources%20Window.md)。  
  
 对于显示在**“数据源”**窗口中的每个数据类型，当你将该项拖到设计器时，都会创建一个默认控件。  在从**“数据源”**窗口拖动项之前，你可以更改将创建的控件。  有关更多信息，请参见[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
## 将控件绑定到数据所涉及的任务  
 下表列出了将控件绑定到数据所需执行的一些最常见任务。  
  
|任务|更多信息|  
|--------|----------|  
|打开**“数据源”**窗口|[如何：打开“数据源”窗口](../data-tools/how-to-open-the-data-sources-window.md)|  
|将数据源添加到项目中|[如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)<br /><br /> [如何：连接到对象中的数据](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)<br /><br /> [如何：连接到服务中的数据](../data-tools/how-to-connect-to-data-in-a-service.md)|  
|设置在将项从**“数据源”**窗口拖到设计器时创建的控件。|[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|修改与**“数据源”**窗口中的项关联的控件的列表。|[向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|创建数据绑定控件。|[在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)<br /><br /> [在 Visual Studio 中将 Silverlight 控件绑定到数据](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)|  
  
 创建了绑定到数据的控件之后，你可能需要执行以下任务之一。  
  
|任务|更多信息|  
|--------|----------|  
|编辑基础数据源中的数据|[在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)|  
|验证对数据所做的更改|[验证数据](../Topic/Validating%20Data.md)|  
|将更新后的数据保存回数据库|[保存数据](../data-tools/saving-data.md)|  
  
## 请参阅  
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [在 Visual Studio 中将 Silverlight 控件绑定到数据](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)   
 [如何：将控件绑定到数据库中的图片](../data-tools/bind-controls-to-pictures-from-a-database.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)   
 [Visual Studio 中用于处理数据源的工具](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)