---
title: "在 Visual Studio 中将 WPF 控件绑定到数据 | Microsoft Docs"
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
  - "数据 [WPF], 显示"
  - "数据绑定, WPF"
  - "显示数据, WPF"
  - "WPF [WPF], 数据"
  - "WPF 数据绑定 [Visual Studio]"
  - "WPF 设计器, 数据绑定"
  - "WPF, Visual Studio 中的数据绑定"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual Studio 中将 WPF 控件绑定到数据
通过将数据绑定到 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 控件，可以向应用程序的用户显示数据。  若要创建这些数据绑定控件，您可以在  **中将[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]“数据源”**窗口上的项拖动到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]上。  本主题将介绍一些您可用于创建数据绑定 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 应用程序的最常见的任务、工具和类。  
  
 有关如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建数据绑定控件的一般信息，请参阅[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。 有关 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 数据绑定的详细信息，请参阅[数据绑定概述](../Topic/Data%20Binding%20Overview.md)。  
  
## 将 WPF 控件绑定到数据所涉及的任务  
 下表列出了可以通过将项从**“数据源”**窗口拖到 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]中来完成的任务。  
  
|任务|更多信息|  
|--------|----------|  
|新建数据绑定控件。<br /><br /> 将现有控件绑定到数据。|[如何：在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|创建按父子关系显示相关数据的控件：当用户选择一个控件中的父数据记录时，另一个控件将显示所选记录的相关子数据。|[如何：在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)|  
|创建一个查找表，此表根据一个表的外键字段的值显示另一个表中的信息。|[如何：在 WPF 应用程序中创建查找表](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|将控件绑定到数据库中的图像。|[如何：将控件绑定到数据库中的图片](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## 有效放置目标  
 只能将**“数据源”**窗口中的项拖动到 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]中的有效放置目标。  有两种主要的有效放置目标：容器和控件。  容器是通常包含控件的用户界面元素。  例如，网格是容器，窗口也是容器。  
  
## 生成的 XAML 和代码  
 将**“数据源”**窗口中的项拖到 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]中时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将生成定义新的数据绑定控件（或将现有控件绑定到数据源）的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]。  对于某些数据源，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 还将在代码隐藏文件中生成用数据填充数据源的代码。  
  
 下表列出了 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 为[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]“数据源”窗口中的每种类型的数据源生成的  **和代码。**  
  
|数据源|生成将控件绑定到数据源的 XAML|生成用数据填充数据源的代码|  
|---------|-----------------------|-------------------|  
|数据集|是|是|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|是|是|  
|服务|是|No|  
|对象|是|No|  
  
### 数据集  
 将表或列从**“数据源”**窗口拖到设计器中时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将生成可执行以下操作的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]：  
  
-   将数据集和新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。  <xref:System.Windows.Data.CollectionViewSource> 是可用于导航和显示数据集中的数据的对象。  
  
-   为控件创建数据绑定。  如果将项拖动到设计器中的一个现有控件上，则 XAML 会将该控件绑定到该项。  如果将项拖动到容器中，则 XAML 将创建为所拖动的项选择的控件，并将该控件绑定到该项。  将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 还将对代码隐藏文件做出以下更改：  
  
-   为包含该控件的 <xref:System.Windows.FrameworkElement.Loaded> 元素创建 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件处理程序。  该事件处理程序用数据填充表，从容器的资源中检索 <xref:System.Windows.Data.CollectionViewSource>，然后使第一个数据项成为当前项。  如果已存在 <xref:System.Windows.FrameworkElement.Loaded> 事件处理程序，则 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会将此代码添加到现有的事件处理程序中。  
  
### 实体数据模型  
 将实体或实体属性从**“数据源”**窗口拖到设计器中时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将生成执行以下操作的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]：  
  
-   将新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。  <xref:System.Windows.Data.CollectionViewSource> 是可用于导航和显示实体中的数据的对象。  
  
-   为控件创建数据绑定。  如果将项拖动到设计器中的一个现有控件上，则 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 会将该控件绑定到该项。  如果将项拖动到容器中，则 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 将创建为所拖动的项选择的控件，并将该控件绑定到该项。  将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
 Visual Studio 还将对代码隐藏文件做出以下更改：  
  
-   添加一种新方法，该方法返回对拖动到设计器中的实体（或包含拖动到设计器中的属性的实体）的查询。  该新方法的名称为 Get*EntityName*Query，其中 *EntityName* 是该实体的名称。  
  
-   为包含该控件的 <xref:System.Windows.FrameworkElement.Loaded> 元素创建 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件处理程序。  该事件处理程序调用 Get*EntityName*Query 方法，以用数据填充该实体，从容器的资源中检索 <xref:System.Windows.Data.CollectionViewSource>，然后使第一个数据项成为当前数据项。  如果已存在 <xref:System.Windows.FrameworkElement.Loaded> 事件处理程序，则 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会将此代码添加到现有的事件处理程序中。  
  
### 服务  
 将某个服务对象或属性从**“数据源”**窗口拖到设计器中时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将生成创建数据绑定控件（或将现有控件绑定到该对象或属性）的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]。  但是，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不会生成用数据填充代理服务对象的代码。  您必须自己编写此代码。  有关演示如何执行此操作的示例，请参阅[演练：将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。  
  
 Visual Studio 将生成执行以下操作的 XAML：  
  
-   将新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。  <xref:System.Windows.Data.CollectionViewSource> 是一个对象，它可用于导航和显示服务返回的对象中的数据。  
  
-   为控件创建数据绑定。  如果将项拖动到设计器中的一个现有控件上，则 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 会将该控件绑定到该项。  如果将项拖动到容器中，则 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 将创建为所拖动的项选择的控件，并将该控件绑定到该项。  将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
### 对象  
 将某个对象或属性从**“数据源”**窗口拖到设计器中时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将生成创建数据绑定控件（或将现有控件绑定到该对象或属性）的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]。  但是，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不会生成用数据填充对象的代码。  您必须自己编写此代码。  
  
> [!NOTE]
>  自定义类必须是公共的且具有默认的无参数构造函数。  它们不能是其语法中具有“dot”的嵌套类。  有关详细信息，请参阅 [XAML 及 WPF 的自定义类](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md)。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将生成执行以下操作的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]：  
  
-   将新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。  <xref:System.Windows.Data.CollectionViewSource> 是可用于导航和显示对象中的数据的对象。  
  
-   为控件创建数据绑定。  如果将项拖动到设计器中的一个现有控件上，则 XAML 会将该控件绑定到该项。  如果将项拖动到容器中，则 XAML 将创建为所拖动的项选择的控件，并将该控件绑定到该项。  将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
## 请参阅  
 [如何：在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [如何：在 WPF 应用程序中创建查找表](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [如何：在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)   
 [将 WPF 控件绑定到实体数据模型](http://msdn.microsoft.com/data/jj574514.aspx)   
 [演练：将 WPF 控件绑定到数据集](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [演练：将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [演练：在 WPF 应用程序中显示相关数据](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [“数据源”窗口](../Topic/Data%20Sources%20Window.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)