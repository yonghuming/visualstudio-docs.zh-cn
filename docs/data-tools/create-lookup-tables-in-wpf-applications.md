---
title: "WPF 应用程序中创建查找表 |Microsoft 文档"
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 78322512fdc59b4ba661bca0d40d1532ac4c98e2
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF 应用程序中创建查找表
术语*查找表*(有时称为*查找绑定*) 描述显示从另一个表中的外键字段的值的一个数据表的信息的控件。 你可以通过将父表的主节点中创建查找表或对象中**数据源**窗口拖动到控件已绑定到一个列或相关的子表中的属性。  
  
例如，假设有一个表的`Orders`销售数据库中。 在每个记录`Orders`表包括`CustomerID`，该值指示下订单的哪些客户。 `CustomerID`是点到客户记录中的外键`Customers`表。 显示从订单的列表时`Orders`表，你可能希望显示实际的客户名而不是`CustomerID`。 由于客户名包含在`Customers`表，你需要创建一个查找表来显示客户姓名。 查找表使用`CustomerID`中的值`Orders`记录导航关系，并返回客户名称。  
  
## <a name="to-create-a-lookup-table"></a>创建查找表的步骤  
  
1.  向项目中添加具有相关数据的数据源的以下类型之一：  
  
    -   数据集或实体数据模型。 
  
    -   WCF 数据服务，WCF 服务或 Web 服务。 有关详细信息，请参阅[如何： 连接到服务中的数据](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
    -   对象。 有关详细信息，请参阅[绑定到 Visual Studio 中的对象](bind-objects-in-visual-studio.md)。  
  
    > [!NOTE]
    >  你可以创建查找表之前，必须作为项目的数据源存在两个相关的表或对象。  
  
2.  打开**WPF 设计器**，并确保该设计器包含有效的放置目标中的项的容器**数据源**窗口。  
  
     有关有效放置目标的详细信息，请参阅[绑定 WPF 控件添加到 Visual Studio 中的数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。  
  
3.  上**数据**菜单上，单击**显示数据源**以打开**数据源**窗口。  
  
4.  展开中的节点**数据源**窗口中，直到可以看到父表或对象和相关的子表或对象。  
  
    > [!NOTE]
    >  相关的子表或对象是显示为在父表或对象的可展开的子节点的节点。  
  
5.  单击子节点的下拉列表菜单，然后选择**详细信息**。  
  
6.  展开子节点。  
  
7.  在下，子节点中，单击相关子与父数据的项的下拉列表菜单。 (在前面的示例中，这是**CustomerID**节点。)选择以下类型的控件以及支持查找绑定之一：  
  
    -   **组合框**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  如果**ListBox**或**ListView**控件未出现在列表中，你可以将这些控件添加到列表。 有关信息，请参阅[设置从数据源窗口拖动时创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
    -   派生自任何自定义控件<xref:System.Windows.Controls.Primitives.Selector>。  
  
        > [!NOTE]
        >  若要添加自定义控件添加到控件的列表你了解如何可以选择中的项**数据源**窗口中，请参阅[将自定义控件添加到数据源窗口](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
8.  将从子节点**数据源**窗口拖到 WPF 设计器中的容器。 (在前面的示例中，子节点是**订单**节点。)  
  
     Visual Studio 将生成为每个您拖动的项创建新的数据绑定控件的 XAML。 XAML 还将添加一个新<xref:System.Windows.Data.CollectionViewSource>子表或到放置目标的资源的对象。 对于某些数据源，Visual Studio 还会生成代码以将数据加载到表或对象。 有关详细信息，请参阅[绑定 WPF 控件添加到 Visual Studio 中的数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。  
  
9. 将从父节点**数据源**窗口拖到前面创建的查找绑定控件。 (在前面的示例中，该父节点是**客户**节点)。  
  
     Visual Studio 设置来配置查找绑定控件上的某些属性。 下表列出了 Visual Studio 会修改的属性。 如有必要，你可以更改这些属性采用 XAML 或**属性**窗口。  
  
    |属性|设置说明|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|此属性指定的集合或用于获取在控件中显示的数据的绑定。 Visual Studio 将此属性设置为<xref:System.Windows.Data.CollectionViewSource>拖到控件的父数据。|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|此属性指定在控件中显示的数据项的路径。 Visual Studio 后为主键，具有字符串数据类型将此属性设置为第一列或父数据中的属性。<br /><br /> 如果你想要在父数据中显示不同的列或属性，则将此属性更改为的另一个属性的路径。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 将此属性绑定到的列或拖动到设计器的子数据的属性。 这是父数据的外键。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio 将此属性设置为列的路径或外键到父数据的子数据属性。|  
  
## <a name="see-also"></a>请参阅
[将 WPF 控件绑定到 Visual Studio 中的数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[WPF 应用程序中显示相关的数据](../data-tools/display-related-data-in-wpf-applications.md)   
[演练：在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)