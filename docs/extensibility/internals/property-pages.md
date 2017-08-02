---
title: "属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更改属性的配置选项"
  - "属性页"
  - "属性页中，更改配置选项"
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 属性页
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

用户可以查看和更改项目配置相关和 \- 独立属性使用属性页。  **属性页** 按钮均处于启用状态在 **属性** 窗口或在解决方案的选定的对象的属性页视图的对象资源管理器工具栏。  属性页由环境创建并为解决方案和项目可用。  它们可能，不过，还能够为利用配置相关属性的项目项。  此功能，当在项目中需要的文件不同的编译器交换机设置适当生成时，可以使用。  
  
## 使用属性页  
 如果属性页已显示和选择更改 \(例如，从到项目的解决方案\)，在页信息图中显示新的属性。  如果不支持属性页在对象的特性，则页为空。  
  
 如果多个对象为所有选定的项时，属性页显示特性的交集。  如果选定的项不包含配置相关属性，并在解决方案资源管理器工具栏中 **属性页** 单击按钮，焦点更改为 " 属性 " 窗口。  有关与属性窗口并选择相关的更多信息，请参见 [将属性扩展](../../extensibility/internals/extending-properties.md)。  
  
 如果属性为多个对象显示，并将属性页的值，所有对象的值设置为新值，即使最初是不同的，因此页是空白，作为单个对象的属性中显示的。  
  
 具有 **项目属性页** 对话框的两种泛型类型中可用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  使用字段布局，如下面的屏幕快照所示，在第一， Visual Basic 项目中，例如，属性将显示页，。  在第二个集合中，后面显示在本节中，这些类用于属性网格类似于在 " 属性 " 窗口中找到的数据。  
  
 ![Visual Basic 属性页](~/docs/extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
项目属性具有字段布局和树结构的页 " 对话框  
  
 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>， " 属性页 " 对话框中的树结构不进行生成。  环境，具体取决于级别名称传递给它 <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> 接口，对其进行编译。  
  
 只有两个顶级类可在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 属性页:  
  
-   通用属性，会显示选定的对象的独立于配置的信息。  因此，，在一个公共属性子类别时，配置、平台和配置管理器选项在对话框的顶部水平不可用。  
  
-   配置属性，包含配置相关信息与解决方案或项目的调试、优化和编译参数相关。  
  
 不能创建任何其他的顶级类，但是，可以选择不显示具体在 `IVsPropertyPage`的实现。  如果为，则例如，您没有任何独立于配置的属性公开为对象，可以选择不公开公共属性类。  您显示公共属性，如果 `ISpecifyPropertyPages` 从项目中实现浏览对象和配置属性，当您实现在配置对象 \(实现 `IVsCfg`、 `IVsProjectCfg`和相关接口的对象\) `ISpecifyPropertyPages` 。  
  
 每个类别显示在顶级类别下表示单独的属性页。  类别和子类别项可用在对话框取决于 `ISpecifyPropertyPages` 和 `IVsPropertyPage`的实现。  
  
 在属性中显示的属性的项目的`IDispatch` 对象在选择容器调用实现 `ISpecifyPropertyPages` 枚举类 ID 列表。  类 ID 将作为变量传递给 `ISpecifyPropertyPages` 和用于实例化属性页。  在对话框的左侧，类 ID 列表还传递给 `IVsPropertyPage` 创建树结构。  属性页然后将信息传递回 `IDispatch` 对象实现 `ISpecifyPropertyPages` 并加载每页的信息。  
  
 浏览对象的属性检索使用每个对象的 `IDispatch` 在选择容器。  
  
 实现在 VSPackage 中 `Help::DisplayTopicFromF1Keyword` 为帮助按钮的功能。  
  
 有关更多信息，请参见 MSDN library 中的 `IDispatch` 和 `ISpecifyPropertyPages`。  
  
 如下面的屏幕快照所示，属性页的第二种类型的示例宿主公开的属性网格的窗体，。  
  
 ![VC 属性页](~/docs/extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
属性调用具有属性网格的对话框  
  
 接口 `IVSMDPropertyBrowser` 和 `IVSMDPropertyGrid` \(声明在 vsmanaged.h\) 用于创建和填充在对话框或窗口中的属性网格。  
  
 项目体系结构与 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的过去版本下载大量已更改。  具体而言，概念的项目处于活动状态已更改。  在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，则不执行任何操作项目的概念。  在无论上下文，生成和部署命令将默认为以前的开发环境中，事件项目是项目。  现在，解决方案控件并仲裁生成和部署命令适用于项。  
  
 的前面是活动项目在三种方式之一将捕获:  
  
-   启动项目  
  
     可以指定项目或从启动的解决方案的属性的项调用，当用户按 F5 或选择运行在 " 生成 " 菜单时。  可以这样做类似的旧事件项目来讲，其名称与粗体的解决方案资源管理器中显示。  
  
     可以检索启动项目作为在自动化模型中的属性通过调用 `DTE.Solution.SolutionBuild.StartupProjects`。  在 VSPackage，请调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 方法。  `IVsSolutionBuildManager` 可用作服务由 SID\_SVsSolutionBuildManager 的 `QueryService` 。  有关更多信息，请参见[项目配置对象](../../extensibility/internals/project-configuration-object.md)和 [解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
-   活动解决方案生成配置  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 有一个活动解决方案配置，可用于自动化模型通过实现 `DTE.Solution.SolutionBuild.ActiveConfiguration`。  解决方案配置是解决方案包含每个项目的项目配置的集合 \(每个项目可能有多个配置，在多个平台，具有不同的名称\)。  有关与解决方案的属性页相关的更多信息，请参见 [解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
-   当前选定项  
  
     执行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 方法检索选定的项目层次结构和项目项或项目。  从 DTE，您将使用 `SelectedItems.SelectedItem.Project` 和 `SelectedItems.SelectedItem.ProjectItem` 方法。  代码示例包括在内核将 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的这些标题下文档。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [项目配置对象](../../extensibility/internals/project-configuration-object.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)