---
title: "将 WPF 控件绑定到 Visual Studio 的第 1 部分中的数据 |Microsoft 文档"
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 685f57286a022be6b7acbdaf2b8ffed33457fef1
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>将 WPF 控件绑定到 Visual Studio 中的数据
通过将数据绑定到 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 控件，可以向应用程序的用户显示数据。 若要创建这些数据绑定控件，可以将某些项从**数据源**窗口拖到[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 本主题将介绍一些您可用于创建数据绑定 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 应用程序的最常见的任务、工具和类。  
  
 有关如何创建数据绑定控件中的常规信息[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，请参阅[将控件绑定到 Visual Studio 中的数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。 有关详细信息[!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]数据绑定，请参阅[数据绑定概述](/dotnet/framework/wpf/data/data-binding-overview)。  
  
## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>所涉及的 WPF 控件绑定到数据任务  
 下表列出可以通过将某些项从来完成的任务**数据源**窗口[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]。  
  
|任务|更多信息|  
|----------|----------------------|  
|新建数据绑定控件。<br /><br /> 将现有控件绑定到数据。|[将 WPF 控件绑定到数据集](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|创建按父子关系显示相关数据的控件：当用户选择一个控件中的父数据记录时，另一个控件将显示所选记录的相关子数据。|[在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)|  
|创建*查找表*显示从另一个表中的外键字段的值的一个表的信息。|[在 WPF 应用程序中创建查找表](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|将控件绑定到数据库中的图像。|[将控件绑定到数据库中的图片](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## <a name="valid-drop-targets"></a>有效放置目标  
 你可以将项中**数据源**仅对中的有效放置目标的窗口[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]。 有两种主要的有效放置目标：容器和控件。 容器是通常包含控件的用户界面元素。 例如，网格是容器，窗口也是容器。  
  
## <a name="generated-xaml-and-code"></a>生成的 XAML 和代码  
 中的项的拖时**数据源**窗口[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]定义了一个新的数据绑定控件 （或将现有控件绑定到数据源）。 对于某些数据源，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 还将在代码隐藏文件中生成用数据填充数据源的代码。  
  
 下表列出[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]和代码[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]为每种类型的数据源中生成**数据源**窗口。  
  
|数据源|生成将控件绑定到数据源的 XAML|生成用数据填充数据源的代码|  
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|  
|数据集|是|是|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|是|是|  
|服务|是|No|  
|对象|是|No|  
  
### <a name="datasets"></a>数据集  
 将表或列从**数据源**到设计器中，窗口[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]可执行以下：  
  
-   将数据集和新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。 <xref:System.Windows.Data.CollectionViewSource> 是可用于导航和显示数据集中的数据的对象。  
  
-   为控件创建数据绑定。 如果将项拖动到设计器中的一个现有控件上，则 XAML 会将该控件绑定到该项。 如果将项拖动到容器中，则 XAML 将创建为所拖动的项，选择的控件并将控件绑定到项。 将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 还将对代码隐藏文件做出以下更改：  
  
-   为包含该控件的 <xref:System.Windows.FrameworkElement.Loaded> 元素创建 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件处理程序。 该事件处理程序用数据填充表，从容器的资源中检索 <xref:System.Windows.Data.CollectionViewSource>，然后使第一个数据项成为当前项。 如果<xref:System.Windows.FrameworkElement.Loaded>事件处理程序已存在，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将此代码添加到现有的事件处理程序。  
  
### <a name="entity-data-models"></a>实体数据模型  
 当您将一个实体或实体属性从**数据源**到设计器中，窗口[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]可执行以下：  
  
-   将新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。 <xref:System.Windows.Data.CollectionViewSource> 是可用于导航和显示实体中的数据的对象。  
  
-   为控件创建数据绑定。 如果将项拖动到设计器中的一个现有控件上，则 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 会将该控件绑定到该项。 如果你将项拖动到容器中，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]创建控件，为拖动的项中，选择并将控件绑定到项。 将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
Visual Studio 还将对代码隐藏文件做出以下更改：  
  
-   添加一种新方法，该方法返回对拖动到设计器中的实体（或包含拖动到设计器中的属性的实体）的查询。 新的方法具有的名称为 Get*EntityName*查询，其中*EntityName*是实体的名称。  
  
-   为包含该控件的 <xref:System.Windows.FrameworkElement.Loaded> 元素创建 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件处理程序。 事件处理程序调用 Get*EntityName*Query 方法以用数据，检索填充该实体<xref:System.Windows.Data.CollectionViewSource>从容器的资源，然后使第一个数据项的当前项。 如果<xref:System.Windows.FrameworkElement.Loaded>事件处理程序已存在，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将此代码添加到现有的事件处理程序。  
  
### <a name="services"></a>服务  
 将服务对象或属性从**数据源**到设计器中，窗口[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]创建数据绑定控件 （或将现有控件绑定到对象或属性）。 但是，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不会生成用数据填充代理服务对象的代码。 你必须自己编写此代码。 有关演示如何执行此操作的示例，请参阅[绑定 WPF 控件添加到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。  
  
 Visual Studio 将生成执行以下操作的 XAML：  
  
-   将新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。 <xref:System.Windows.Data.CollectionViewSource> 是一个对象，它可用于导航和显示服务返回的对象中的数据。  
  
-   为控件创建数据绑定。 如果将项拖动到设计器中的一个现有控件上，则 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 会将该控件绑定到该项。 如果你将项拖动到容器中，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]创建控件，为拖动的项中，选择并将控件绑定到项。 将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
### <a name="objects"></a>对象  
 当拖动的对象或属性从**数据源**到设计器中，窗口[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]创建数据绑定控件 （或将现有控件绑定到对象或属性）。 但是，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不会生成用数据填充对象的代码。 你必须自己编写此代码。  
  
> [!NOTE]
>  自定义的类都必须是公共的并且默认情况下，具有无参数构造函数。 它们 can'tbe 嵌套类，其语法中有一个"点"。 有关详细信息，请参阅[XAML 和 wpf 自定义类](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf)。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]可执行以下：  
  
-   将新的 <xref:System.Windows.Data.CollectionViewSource> 添加到将项拖至的容器的资源中。 <xref:System.Windows.Data.CollectionViewSource> 是可用于导航和显示对象中的数据的对象。  
  
-   为控件创建数据绑定。 如果将项拖动到设计器中的一个现有控件上，则 XAML 会将该控件绑定到该项。 如果将项拖动到容器中，则 XAML 将创建为所拖动的项，选择的控件并将控件绑定到项。 将在新的 <xref:System.Windows.Controls.Grid> 内创建该控件。  
  
## <a name="see-also"></a>请参阅
[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)
