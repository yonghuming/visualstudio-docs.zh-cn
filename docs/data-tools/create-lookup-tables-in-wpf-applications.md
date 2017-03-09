---
title: "如何：在 WPF 应用程序中创建查找表 | Microsoft Docs"
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 WPF 应用程序中创建查找表
通过将**“数据源”**窗口中的父表或父对象的主节点拖动到一个已绑定到相关子表中的列或属性的控件，可以创建查找表。  术语“查找表”（有时称作“查找绑定”）描述了一个控件，该控件根据一个数据表中的外键字段的值显示另一个数据表中的信息。  
  
 例如，考虑一个销售数据库中的 `Orders` 表。  `Orders` 表中的每条记录都包含一个用于指示下订单的客户的 `CustomerID`。  `CustomerID` 是一个指向 `Customers` 表中的客户记录的外键。  当从 `Orders` 表中显示订单列表时，您可能希望显示实际的客户名而不是 `CustomerID`。  由于客户名包含在 `Customers` 表中，因此您需要创建一个查找表来显示客户名。  查找表使用 `Orders` 记录中的 `CustomerID` 值来导航关系并返回用户友好的客户名。  
  
### 创建查找表  
  
1.  将带有相关数据的以下类型之一的数据源添加到项目中：  
  
    -   数据集或实体数据模型。  有关更多信息，请参见[如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)。  
  
    -   WCF 数据服务、WCF 服务或 Web 服务。  有关更多信息，请参见[如何：连接到服务中的数据](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
    -   对象。  有关更多信息，请参见[如何：连接到对象中的数据](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)。  
  
    > [!NOTE]
    >  必须有两个相关表或对象作为项目的数据源，您才能创建查找表。  
  
2.  打开 WPF 设计器，并确保设计器包含一个作为**“数据源”**窗口中的项的有效放置目标的容器。  
  
     有关有效放置目标的更多信息，请参见[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
3.  在**“数据”**菜单上单击**“显示数据源”**，打开**“数据源”**窗口。  
  
4.  展开**“数据源”**窗口中的节点，直到您可以看到父表或父对象，以及相关的子表或子对象。  
  
    > [!NOTE]
    >  相关的子表或子对象是在父表或父对象下显示为可展开子节点的节点。  
  
5.  单击子节点的下拉菜单，然后选择**“详细信息”**。  
  
6.  展开子节点。  
  
7.  在子节点下，单击与子数据和父数据相关的项的下拉菜单（在上述示例中，子节点为**“CustomerID”**节点）。  选择支持查找绑定的以下类型之一的控件：  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  如果列表中没有显示**“ListBox”**或**“ListView”**控件，则可以向列表中添加这些控件。  有关信息，请参见[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
    -   派生自 <xref:System.Windows.Controls.Primitives.Selector> 的任何自定义控件。  
  
        > [!NOTE]
        >  有关如何将自定义控件添加到可为**“数据源”**窗口中的项选择的控件列表的信息，请参见[向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
8.  将子节点从**“数据源”**窗口拖动到 WPF 设计器中的容器上方（在上述示例中，子节点为**“Orders”**节点）。  
  
     Visual Studio 会生成 XAML，它将为拖动的每个项创建一个新的数据绑定控件。  XAML 还会将子表或子对象的新 <xref:System.Windows.Data.CollectionViewSource> 添加到放置目标的资源中。  对于某些数据源，Visual Studio 还会生成代码以将数据加载到表或对象中。  有关更多信息，请参见[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
9. 将父节点从**“数据源”**窗口拖动到先前创建的查找绑定控件上（在上述示例中，父节点为**“Customers”**节点）。  
  
     Visual Studio 会设置该控件的一些属性以配置查找绑定。  下表列出了 Visual Studio 修改的属性。  如有必要，可在 XAML 中或**“属性”**窗口中更改这些属性。  
  
    |属性|设置说明|  
    |--------|----------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|此属性指定用于获取控件中显示的数据的集合或绑定。  Visual Studio 会为拖动到控件上的父数据将此属性设置为 <xref:System.Windows.Data.CollectionViewSource>。|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|此属性指定控件中显示的数据项的路径。  Visual Studio 将此属性设置为具有字符串数据类型的父数据中主键后的第一个列或属性。<br /><br /> 如果您希望显示父数据中的其他列或属性，请将此属性更改为其他属性的路径。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 将此属性绑定到您拖动到设计器中的子数据的列或属性。  这是父数据的外键。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio 将此属性设置为子数据的列或属性（作为父数据的外键）的路径。|  
  
## 请参阅  
 [在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [如何：在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)   
 [演练：在 WPF 应用程序中显示相关数据](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)