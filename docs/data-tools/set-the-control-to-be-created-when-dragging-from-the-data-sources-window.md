---
title: "设置从“数据源”窗口中拖动时要创建的控件 | Microsoft Docs"
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
  - "数据源窗口，选择控件"
  - "Windows 窗体，显示数据"
  - "数据 [Visual Studio]，在 Windows 窗体上显示"
  - "数据 [Visual Studio]，“数据源”窗口"
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 31
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 设置从“数据源”窗口中拖动时要创建的控件
您可以通过将项从**“数据源”**窗口拖到 WPF 设计器或 Windows 窗体设计器上来创建数据绑定控件。  **“数据源”**窗口中的每个项都有一个默认控件，当您将该项拖动到设计器中时，将会创建该控件。  不过，您可以选择创建其他控件。  
  
## 设置要为数据表或对象创建的控件  
 在从**“数据源”**窗口拖动表示数据表或对象的项之前，您可以选择在一个控件中显示所有数据，或选择在单独的控件中显示每个列或属性。  
  
 在此上下文中，术语“对象”是指自定义业务对象、实体（在实体数据模型中）或服务返回的对象。  
  
#### 设置要为数据表或对象创建的控件  
  
1.  确保 WPF 设计器或 Windows 窗体设计器已打开。  
  
2.  在**“数据源”**窗口中，选择表示要设置的数据表或对象的项。  
  
3.  单击该项的下拉菜单，然后在菜单中单击以下各项之一：  
  
    -   若要在单独的控件中显示每个数据字段，请单击**“详细信息”**。  在将数据项拖到设计器时，此操作将随每个控件的标签一起为父数据表或对象的每个列或属性创建不同的数据绑定控件。  
  
    -   若要在单个控件中显示所有数据，请在列表中选择不同的控件，例如 WPF 应用程序中的**“DataGrid”**或**“List”**，或 Windows 窗体应用程序中的**“DataGridView”**。  
  
     可用控件的列表取决于您已打开的设计器、项目所面向的 .NET Framework 的版本，以及您是否已将支持数据绑定的自定义控件添加到**“工具箱”**。  如果要创建的控件位于可用控件的列表中，您可以将该控件添加到列表。  有关详细信息，请参阅[向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
     若要了解如何创建可为**“数据源”**窗口中的数据表或对象添加到控件列表的自定义 Windows 窗体控件，请参见[演练：创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。  
  
## 设置要为数据列或属性创建的控件  
 在将表示对象的列或属性的项从**“数据源”**窗口拖到设计器之前，您可以设置要创建的控件。  
  
#### 设置要为列或属性创建的控件  
  
1.  确保 WPF 设计器或 Windows 窗体设计器已打开。  
  
2.  在**“数据源”**窗口中，展开所需的表或对象以显示它的列或属性。  
  
3.  选择要为其设置要创建的控件的每个列或属性。  
  
4.  单击该列或属性的下拉菜单，然后选择要在将项拖到设计器时创建的控件。  
  
     可用控件的列表取决于您已打开的设计器、项目所面向的 .NET Framework 的版本，以及您已添加到**“工具箱”**的支持数据绑定的自定义控件。  如果要创建的控件位于可用控件的列表中，您可以将该控件添加到列表。  有关详细信息，请参阅[向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
     若要了解如何创建可为**“数据源”**窗口中的数据列或属性添加到控件列表的自定义控件，请参见[演练：创建支持简单数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)。  
  
     如果不希望为列或属性创建控件，请在下拉菜单中选择**“无”**。  如果要将父表或对象拖到设计器但不希望包括特定列或属性，则这样做非常有用。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [“数据源”窗口](../Topic/Data%20Sources%20Window.md)   
 [向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)