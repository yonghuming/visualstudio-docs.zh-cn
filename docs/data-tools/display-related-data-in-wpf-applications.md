---
title: "如何：在 WPF 应用程序中显示相关数据 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "数据 [WPF], 显示"
  - "数据绑定, WPF"
  - "显示数据, WPF"
  - "WPF [WPF], 数据"
  - "WPF 数据绑定 [Visual Studio]"
  - "WPF 设计器, 数据绑定"
  - "WPF, Visual Studio 中的数据绑定"
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 WPF 应用程序中显示相关数据
在某些应用程序中，您可能需要处理来自多个表或实体（这些表或实体以父子关系相互关联）中的数据。  例如，您可能要显示一个显示来自 `Customers` 表中的客户的网格。  当用户选择某个特定客户时，另一个网格将从一个相关的 `Orders` 表中显示该客户的订单。  
  
 通过将项从**“数据源”**窗口拖到 WPF 设计器中，可以创建显示相关数据的数据绑定控件。  
  
### 创建显示相关记录的控件  
  
1.  在**“数据”**菜单上单击**“显示数据源”**，打开**“数据源”**窗口。  
  
2.  单击**“添加新数据源”**并完成**“数据源配置向导”**。  
  
3.  打开 WPF 设计器，并确保设计器包含一个作为**“数据源”**窗口中的项的有效放置目标的容器。  
  
     有关有效放置目标的更多信息，请参见[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
4.  在**“数据源”**窗口中，展开表示关系中的父表或父对象的节点。  父表或父对象位于一对多关系中的“一”端。  
  
5.  将父节点（或父节点中的任何单个项）从**“数据源”**窗口拖到设计器的有效放置目标中。  
  
     Visual Studio 会生成 XAML，它将为您拖动的每个项创建一个新的数据绑定控件。  XAML 还会将父表或父对象的新 <xref:System.Windows.Data.CollectionViewSource> 添加到放置目标的资源中。  对于某些数据源，Visual Studio 还会生成代码以将数据加载到父表或父对象中。  有关更多信息，请参见[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
6.  在**“数据源”**窗口中，找到相关子表或子对象。  相关子表和子对象作为可展开节点显示在父节点的数据列表的底部。  
  
7.  将子节点（或子节点中的任何单个项）从**“数据源”**窗口拖到设计器的有效放置目标中。  
  
     Visual Studio 会生成 XAML，它将为您拖动的每个项创建一个新的数据绑定控件。  XAML 还会将子表或子对象的新 <xref:System.Windows.Data.CollectionViewSource> 添加到放置目标的资源中。  此新的 <xref:System.Windows.Data.CollectionViewSource> 将绑定到您刚刚拖动到设计器中的父表或父对象的属性上。  对于某些数据源，Visual Studio 还会生成代码以将数据加载到子表或子对象中。  
  
     下图演示了**“数据源”**窗口的数据集中的**“Customers”**表的相关**“Orders”**表。  
  
     ![显示关系的数据源窗口](~/data-tools/media/datasources2.gif "DataSources2")  
  
## 请参阅  
 [在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [如何：在 WPF 应用程序中创建查找表](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [演练：在 WPF 应用程序中显示相关数据](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)