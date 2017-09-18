---
title: "如何：将 Windows 窗体控件绑定到数据 | Microsoft Docs"
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
  - "数据 [Windows 窗体], 显示"
  - "数据源, 显示"
  - "显示数据, Windows 窗体控件"
  - "Windows 窗体, 显示数据"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将 Windows 窗体控件绑定到数据
通过从[“数据源”窗口](../Topic/Data%20Sources%20Window.md)拖动对象，将数据绑定到 Windows 窗体控件。  在从**“数据源”**窗口拖动项之前，您可以为各个控件或 <xref:System.Windows.Forms.DataGridView> 的**“DataGridView”**将表的控件类型设置为**“详细信息”**。  有关更多信息，请参见[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
 如果应用程序需要的控件不可从 **\*\*\* 数据源 \*\*\*** 窗口中，可以添加控件。  有关更多信息，请参见[向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 在单个控件中显示整个数据表  
 通过将表（或表示使用对象数据源时的连接的节点）从**“数据源”**窗口拖到 Windows 应用程序窗体，可以在单个控件中显示整个数据表。  
  
#### 显示整个数据表  
  
1.  打开**“数据源”**窗口。  有关更多信息，请参见[如何：打开“数据源”窗口](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果**“数据源”**窗口是空的，请在该窗口中添加一个数据源。  有关更多信息，请参见 [数据源概述](../data-tools/add-new-data-sources.md)。  
  
2.  在**“Windows 窗体设计器”**中打开窗体。  
  
3.  在**“数据源”**窗口中选择表，单击下拉键头，然后选择**“详细信息”**。  
  
4.  将表从**“数据源”**窗口拖到窗体上。  
  
     即在该窗体上为每列或每个属性创建了单个数据绑定控件，该控件带有具有适当标题的标签控件。  
  
## 在单个控件中显示选中的数据列  
 通过将单个列（或使用对象数据源时的属性）从**“数据源”**窗口拖到 Windows 应用程序窗体，可以在单个控件中显示单个数据列。  
  
#### 显示选择的数据列  
  
1.  打开**“数据源”**窗口。  有关更多信息，请参见[如何：打开“数据源”窗口](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果**“数据源”**窗口是空的，请在该窗口中添加一个数据源。  有关更多信息，请参见 [数据源概述](../data-tools/add-new-data-sources.md)。  
  
2.  展开表来显示单个列。  
  
    > [!TIP]
    >  若要设置为每列创建的控件，请在**“数据源”**窗口中选择列，单击下拉箭头，然后从可用控件列表中选择控件。  有关更多信息，请参见[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
3.  在**“Windows 窗体设计器”**中打开窗体。  
  
4.  将所需列从**“数据源”**窗口拖到窗体上。  
  
     对于拖动的每列或每个属性，即在该窗体上为其创建了单个数据绑定控件，该控件带有具有适当标题的标签控件。  
  
 也可以将项从**“数据源”**窗口拖到现有控件（窗体上已有的控件）上，以将控件绑定到数据。  已绑定到数据的控件会将其数据绑定重置为最近拖动到该控件上的项。  
  
> [!NOTE]
>  控件必须能显示从**“数据源”**窗口拖放的项的基础数据类型才能成为有效的拖放目标。  例如，将数据类型为 <xref:System.DateTime> 的项拖动到 <xref:System.Windows.Forms.CheckBox> 上是无效的，因为 <xref:System.Windows.Forms.CheckBox> 不能显示日期。  
  
#### 将现有控件绑定到数据  
  
1.  打开**“数据源”**窗口。  有关更多信息，请参见[如何：打开“数据源”窗口](../data-tools/how-to-open-the-data-sources-window.md)。  
  
2.  在 [Windows Forms Designer](http://msdn.microsoft.com/zh-cn/3c3d61f8-f36c-4d41-b9c3-398376fabb15) 中打开窗体。  
  
3.  在**“数据源”**窗口展开一个表或对象以显示其自身的列或属性。  
  
4.  将需要的项从**“数据源”**窗口拖动到现有控件上。  
  
     这时，控件绑定到所选项。  
  
## 在 DataGridView 控件中显示数据  
  
#### 在新的 Windows 窗体 DataGridView 控件中显示数据  
  
1.  打开**“数据源”**窗口。  有关更多信息，请参见[如何：打开“数据源”窗口](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果**“数据源”**窗口是空的，请在该窗口中添加一个数据源。  有关更多信息，请参见 [数据源概述](../data-tools/add-new-data-sources.md)。  
  
2.  在**“Windows 窗体设计器”**中打开窗体。  
  
3.  在**“数据源”**窗口中选择表，单击下拉键头，然后选择**“DataGridView”**。  
  
4.  将表从**“数据源”**窗口拖动到窗体。  
  
     用于导航记录的 <xref:System.Windows.Forms.DataGridView> 控件和工具栏（<xref:System.Windows.Forms.BindingNavigator>）出现在窗体上。  组件栏中出现 [DataSet](../data-tools/dataset-tools-in-visual-studio.md)、[TableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator>。  
  
#### 在现有 Windows 窗体 DataGridView 控件中显示数据  
  
1.  打开**“数据源”**窗口。  有关更多信息，请参见[如何：打开“数据源”窗口](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果**“数据源”**窗口是空的，请在该窗口中添加一个数据源。  有关更多信息，请参见 [数据源概述](../data-tools/add-new-data-sources.md)。  
  
2.  在**“Windows 窗体设计器”**中打开窗体。  
  
3.  在**“数据源”**窗口中选择表，单击下拉键头，然后选择**“DataGridView”**。  
  
4.  将表从**“数据源”**窗口拖动到窗体的<xref:System.Windows.Forms.DataGridView> 上。  
  
     <xref:System.Windows.Forms.DataGridView> 控件现在被绑定到已拖动到该控件上的表。  组件栏中出现 [DataSet](../data-tools/dataset-tools-in-visual-studio.md)、[TableAdapter](../data-tools/tableadapter-overview.md) 和 <xref:System.Windows.Forms.BindingSource>。  
  
## 请参阅  
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [BindingSource 组件概述](../Topic/BindingSource%20Component%20Overview.md)   
 [BindingNavigator 控件概述](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)   
 [Visual Studio 中用于处理数据源的工具](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)