---
title: "在 Visual Studio 中将 Windows 窗体控件绑定到数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "数据 [Windows 窗体], 数据源"
  - "数据 [Windows 窗体], 显示"
  - "数据源, 显示数据"
  - "在窗体上显示数据"
  - "显示数据, Windows 窗体"
  - "窗体, 显示数据"
  - "Windows 窗体, 数据绑定"
  - "Windows 窗体, 显示数据"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual Studio 中将 Windows 窗体控件绑定到数据
通过将数据绑定到 Windows 窗体，可以向应用程序的用户显示数据。  若要创建这些数据绑定控件，您可以在 Visual Studio 中将项从**“数据源”**窗口拖到 Windows 窗体设计器上。  本主题将介绍创建数据绑定 Windows 窗体应用程序的过程中所涉及的一些最常见的任务、工具和类。  
  
 有关如何在 Visual Studio 中创建数据绑定控件的一般信息，请参见[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  有关 Windows 窗体中的数据绑定的更多信息，请参见 [Windows 窗体数据绑定](../Topic/Windows%20Forms%20Data%20Binding.md)。  
  
## 在 Windows 应用程序中的窗体上显示数据所涉及的任务  
 下表列出了与在 Windows 应用程序中的窗体上显示数据相关的常见任务。  
  
|任务|更多信息|  
|--------|----------|  
|创建数据绑定控件。<br /><br /> 将现有控件绑定到数据。|[如何：将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data.md)|  
|创建按父子关系显示相关数据的控件：当用户选择一个控件中的数据记录时，另一个控件将显示所选记录的相关数据。|[如何：在 Windows 窗体应用程序中显示相关数据](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)|  
|创建查找表。  查找表可根据另一个表的外键字段的值显示一个表中的信息。|[如何：在 Windows 窗体应用程序中创建查找表](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|设置控件显示数据的方式。|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/zh-cn/42638120-9e6f-436b-985f-4036664230fd)|  
|更改**“数据源”**窗口中智能标题功能的行为。|[如何：自定义 Visual Studio 创建数据绑定控件的标题的方式
](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|添加执行参数化查询的控件。|[如何：向 Windows 窗体应用程序中添加参数化查询](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|设置列以使用图像控件显示数据库中的图像。|[如何：将控件绑定到数据库中的图片](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|在数据集中筛选数据或对数据排序。|[如何：在 Windows 窗体应用程序中对数据进行筛选和排序](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 以下主题提供了将 Windows 窗体控件绑定到数据的示例。  
  
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 提供分步详细说明，介绍如何查询数据库中的数据以及如何在 Windows 窗体上显示数据。  
  
 [演练：在 Windows 窗体上显示相关数据](../Topic/Walkthrough:%20Displaying%20Related%20Data%20on%20a%20Windows%20Form.md)  
 提供分步详细说明，介绍如何显示两个相关表中的数据以及如何在 Windows 窗体上显示该数据。  
  
 [演练：创建用于搜索数据的 Windows 窗体](../data-tools/create-a-windows-form-to-search-data.md)  
 提供有关如何创建 Windows 窗体的分步详细说明，该窗体根据用户输入执行数据库搜索。  
  
 [演练：在 Windows 窗体应用程序中创建查找表](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 提供有关显示一个表中的数据的分步详细说明，该数据基于另一个表中的所选数据。  
  
 [演练：在 Windows 窗体间传递数据](../data-tools/pass-data-between-forms.md)  
 提供分步详细说明，介绍如何在应用程序中从一个窗体向另一个窗体传递值。  
  
 [演练：创建支持简单数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 逐步介绍如何创建可以在**“数据源”**窗口中使用的自定义控件。  
  
 [演练：创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 逐步介绍如何创建可以在**“数据源”**窗口中使用的自定义控件。  
  
 [演练：创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 逐步介绍如何创建可以在**“数据源”**窗口中使用的自定义控件。  
  
## 数据智能标记  
 很多控件上都可以使用用于处理数据的特定智能标记。  将某些控件添加到窗体时，智能标记上提供一组与数据相关的可能操作。  
  
## BindingSource 组件  
 <xref:System.Windows.Forms.BindingSource> 组件有两个用途。  首先，在将窗体上的控件绑定到数据时提供抽象层。  窗体上的控件是绑定到 <xref:System.Windows.Forms.BindingSource> 组件的（而不是直接绑定到数据源）。  
  
 其次，它可管理对象的集合。  将类型添加到 <xref:System.Windows.Forms.BindingSource> 可创建该类型的列表。  
  
 有关 <xref:System.Windows.Forms.BindingSource> 组件的更多信息，请参见：  
  
-   [BindingSource 组件](../Topic/BindingSource%20Component.md)  
  
-   [BindingSource 组件概述](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [BindingSource 组件体系结构](../Topic/BindingSource%20Component%20Architecture.md)  
  
## BindingNavigator 控件  
 此组件提供了用户界面，用于在 Windows 应用程序显示的数据中导航。  有关详细信息，请参阅[BindingNavigator 控件](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md)。  
  
## DataGridView 控件  
 使用 <xref:System.Windows.Forms.DataGridView> 控件可显示和编辑许多不同种类的数据源表格数据。  可通过使用 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 属性将数据绑定到 <xref:System.Windows.Forms.DataGridView>。  有关详细信息，请参阅[DataGridView 控件概述](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md)。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [“数据源”窗口](../Topic/Data%20Sources%20Window.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [演练：创建支持简单数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [演练：创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [演练：创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)