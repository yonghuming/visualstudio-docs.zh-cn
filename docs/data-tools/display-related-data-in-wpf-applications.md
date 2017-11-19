---
title: "WPF 应用程序中显示相关的数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 74acdba4f04dde072d8d34729932596a601f222d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="display-related-data-in-wpf-applications"></a>WPF 应用程序中显示相关的数据
在某些应用程序，你可能想要使用来自多个表或相关的父-子关系中的实体的数据。 例如，你可能想要显示的网格的显示从客户`Customers`表。 当用户选择特定客户时，另一个网格将显示该客户的相关订单`Orders`表。  
  
你可以创建数据绑定控件显示相关的数据，通过将某些项从**数据源**到 WPF 设计器窗口。  
  
## <a name="to-create-controls-that-display-related-records"></a>若要创建显示相关的记录的控件  
  
1.  上**数据**菜单上，单击**显示数据源**以打开**数据源**窗口。  
  
2.  单击**添加新数据源**，并完成**数据源配置**向导。  
  
3.  打开 WPF 设计器中，并确保该设计器包含有效的放置目标中的项的容器**数据源**窗口。  
  
     有关有效放置目标的详细信息，请参阅[绑定 WPF 控件添加到 Visual Studio 中的数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。  
  
4.  在**数据源**窗口中，展开表示父表节点或对象在关系中。 一个对多关系的"一"方上的父表或对象。  
  
5.  从拖动父节点 （或父节点中的任何单个项）**数据源**窗口拖到设计器中的有效放置目标。  
  
     Visual Studio 将生成创建你将每个项的新数据绑定控件的 XAML。 XAML 还将添加一个新<xref:System.Windows.Data.CollectionViewSource>父表或到放置目标的资源的对象。 对于某些数据源，Visual Studio 还会生成代码以将数据加载到父表或对象。 有关详细信息，请参阅[绑定 WPF 控件添加到 Visual Studio 中的数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。  
  
6.  在**数据源**窗口中，找到的相关的子表或对象。 相关的子表和对象显示为数据的父节点的列表底部的可展开节点。  
  
7.  从拖动的子节点 （或子节点中的任何单个项）**数据源**窗口拖到设计器中的有效放置目标。  
  
     Visual Studio 将生成为每个您拖动的项创建新的数据绑定控件的 XAML。 XAML 还将添加一个新<xref:System.Windows.Data.CollectionViewSource>子表或到放置目标的资源的对象。 此新<xref:System.Windows.Data.CollectionViewSource>绑定到父表或您刚刚拖动到设计器的对象的属性。 对于某些数据源，Visual Studio 还会生成代码以将数据加载到子表或对象。  
  
     下图演示了相关**订单**表**客户**中的数据集表**数据源**窗口。  
  
     ![显示关系数据源窗口](../data-tools/media/datasources2.gif "DataSources2")  
  
## <a name="see-also"></a>请参阅
[将 WPF 控件绑定到 Visual Studio 中的数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[WPF 应用程序中创建查找表](../data-tools/create-lookup-tables-in-wpf-applications.md)   
[演练：在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)