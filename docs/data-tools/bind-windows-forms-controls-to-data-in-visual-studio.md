---
title: "将 Windows 窗体控件绑定到 Visual Studio 中的数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 5936edd6096bd708dda1b03f60f94cea3d6c1e5b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>将 Windows 窗体控件绑定到 Visual Studio 中的数据
通过将数据绑定到 Windows 窗体，可以向应用程序的用户显示数据。 若要创建这些数据绑定控件，可以将某些项从**数据源**窗口拖到 Visual Studio 中的 Windows 窗体设计器。
  
![数据源拖动操作](../data-tools/media/raddata-data-source-drag-operation.png "raddata 数据源拖动操作")

拖动项之前，你可以设置你想要将绑定到控件的类型。 具体取决于你选择表本身或对单独列显示不同的值。  你还可以设置自定义值。 对于表，"详细信息"意味着每个列被绑定到一个单独的控件。  

![将数据源绑定到 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata 绑定到 DataGridView 的数据源")  
  
## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource 和 BindingNavigator 控件
<xref:System.Windows.Forms.BindingSource> 组件有两个用途。 首先，它提供一个抽象层时将控件绑定到数据。 表单上的控件绑定到<xref:System.Windows.Forms.BindingSource>组件而不是直接与数据源。 其次，它可以管理的对象的集合。 添加到类型<xref:System.Windows.Forms.BindingSource>创建该类型的列表。  
  
有关详细信息<xref:System.Windows.Forms.BindingSource>组件，请参阅：  
  
-   [BindingSource 组件](/dotnet/framework/winforms/controls/bindingsource-component)  
  
-   [BindingSource 组件概述](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
-   [BindingSource 组件体系结构](/dotnet/framework/winforms/controls/bindingsource-component-architecture)  
  
[BindingNavigator 控件](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)提供用于在 Windows 应用程序显示的数据中导航用户界面。

## <a name="bind-to-data-in-a-datagridview-control"></a>将绑定到 DataGridView 控件中的数据  
有关[DataGridView 控件](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)，整个表绑定到该单个控件。 当将 DataGridView 拖动到窗体中时，一个工具条带用于导航记录 (<xref:System.Windows.Forms.BindingNavigator>) 也会出现。 A[数据集](../data-tools/dataset-tools-in-visual-studio.md)， [TableAdapter](../data-tools/create-and-configure-tableadapters.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。 在下图中，TableAdapterManager 也会添加因为 Customers 表具有与 Orders 表的关系。 这些变量被所有声明的自动生成的代码中为窗体类中的私有成员。 用于填充 DataGridView 自动生成的代码位于 form_load 事件处理程序。 用于保存要更新数据库的数据的代码都位于 BindingNavigator 保存事件处理程序。 可以移动窗口或根据需要修改此代码。  
  
![与 BindingNavigator 的 GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata 与 BindingNavigator 的 GridView")  
  
通过单击中的每个右上角的智能标记，可以自定义 DataGridView 控件与 BindingNavigator 的行为：  
  
![DataGridView 控件与绑定导航器的智能标记](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView 和绑定导航智能标记")  
  
如果未提供控制你的应用程序需要时可从**数据源**窗口中，你可以添加控件。 有关详细信息，请参阅[将自定义控件添加到数据源窗口](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
此外可以将某些项从**数据源**窗口拖动到已在将控件绑定到数据窗体上的控件。 已绑定到数据的控件具有其数据绑定重置为最近拖动到它上面的项。 若要有效放置目标，控件必须能够显示的项拖动到它从上面的基础数据类型的**数据源**窗口。 例如，所以不能拖动项具有数据类型的<xref:System.DateTime>到<xref:System.Windows.Forms.CheckBox>，这是因为<xref:System.Windows.Forms.CheckBox>不能显示日期。  
  
## <a name="bind-to-data-in-individual-controls"></a>将绑定到在单独控件中的数据  
当你将数据源绑定到"详细信息"时，数据集中的每个列绑定到一个单独的控件。  
  
![将数据源绑定到详细信息](../data-tools/media/raddata-bind-data-source-to-details.png "raddata 绑定数据源详细信息")  
  
> [!IMPORTANT]
> 请注意，在上图中，将从客户表不是从 Orders 表的订单属性。 通过绑定到 Customer.Orders 属性，在详细信息控件中可以立即反映在 DataGridView 中进行的导航命令。 如果从订单表拖，这些控件将仍绑定到数据集，但不是它们将不会与同步 DataGridView。  
  
下图中显示的默认的客户表中的订单属性绑定到"详细信息"后添加到窗体数据绑定控件**数据源**窗口。  
  
![Orders 表绑定到详细信息](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders 表绑定到详细信息")  
  
另请注意每个控件具有智能标记。 此标记允许将应用于仅该控件的自定义项。
  
## <a name="see-also"></a>请参阅
[将控件绑定到 Visual Studio 中的数据](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Windows 窗体 (.NET Framework) 中的数据绑定](/dotnet/framework/winforms/windows-forms-data-binding)