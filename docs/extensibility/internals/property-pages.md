---
title: "属性页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 484d53315f836117b69270a2f43b6b780733b9f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="property-pages"></a>属性页
用户可以查看和更改项目依赖于配置和-独立属性使用属性页。 A**属性页**在中启用按钮**属性**窗口或对象，它提供所选对象的属性页面视图的解决方案资源管理器工具栏上。 属性页由环境，可用于解决方案和项目。 它们，但是，也可以是可进行的项目项使用的配置相关的属性。 在项目中的文件需要不同的编译器生成正确的交换机设置时，可能会使用此功能。  
  
## <a name="using-property-pages"></a>使用属性页  
 如果所选内容更改 （例如，从项目的解决方案） 和已显示属性页，显示的信息在页中的更改，以显示新选择的属性。 如果存在该对象上支持属性页的任何属性，属性页将为空。  
  
 如果选择了多个对象，属性页将显示所有选定的项目的属性的交集。 如果所选的项目不包含依赖于配置的属性和**属性页**单击解决方案资源管理器工具栏上的按钮、 焦点更改到属性窗口。 属性窗口中，然后选择与相关的详细信息，请参阅[扩展属性](../../extensibility/internals/extending-properties.md)。  
  
 如果要显示多个对象的属性，更改属性页中的值，所有对象的值都设置为新值中，即使它们是最初不同并显示单个对象的属性时空白页。  
  
 有两种常规类型的**ProjectProperty 页**对话框框中提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 在第一个，对于 Visual Basic 项目，例如，属性页显示使用字段格式，如下面的屏幕截图中所示。 在第二个显示更高版本在此部分中，属性页主机属性网格类似于在属性窗口中找到。  
  
 ![Visual Basic 属性页](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
与字段格式和树的结构的项目属性页对话框  
  
 不使用生成的属性页对话框中的树结构<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 环境中，基于传递给它的级别名称<xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>接口，生成它。  
  
 有只有两个顶级类别可在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]属性页：  
  
-   通用属性，将显示所选的对象或对象的独立于配置的信息。 因此，选中通用属性子类别之一时，沿顶部显示的对话框中的配置、 平台和配置管理器选项不可用。  
  
-   配置属性，其中包含与解决方案或项目的调试、 优化和生成参数相关的配置相关信息。  
  
 无法创建任何其他的顶级类别，但你可以选择不希望显示的实现中的一个或另一个`IVsPropertyPage`。 如果，例如，你没有要显示对象的任何独立于配置的属性，你可以选择不希望显示的通用属性类别。 如果显示通用属性`ISpecifyPropertyPages`实现时，从项的浏览对象和配置属性实现`ISpecifyPropertyPages`配置对象中 (对象实现`IVsCfg`， `IVsProjectCfg`，和相关接口）。  
  
 顶级类别下显示每个类别都表示单独的属性页。 类别和子类别可用项对话框中的由你实现`ISpecifyPropertyPages`和`IVsPropertyPage`。  
  
 `IDispatch`用于选择容器中有要显示在属性页实现的属性的项的对象`ISpecifyPropertyPages`枚举类 Id 的列表。 类 Id 作为变量传递到`ISpecifyPropertyPages`和用于实例化的属性页。 类 Id 的列表还传递给`IVsPropertyPage`左侧的对话框中创建树状结构。 然后，此属性页传递信息回`IDispatch`实现对象`ISpecifyPropertyPages`并填充每个页的信息。  
  
 使用浏览对象的属性进行检索`IDispatch`选择容器中每个对象。  
  
 实现`Help::DisplayTopicFromF1Keyword`中你的 VSPackage 提供的功能帮助按钮。  
  
 有关详细信息，请参阅`IDispatch`和`ISpecifyPropertyPages`MSDN 库中。  
  
 第二个类型的属性页显示在示例主机一种形式的属性网格中，如下面的屏幕截图中所示。  
  
 ![VC 属性页](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
与属性网格的属性页对话框  
  
 接口`IVSMDPropertyBrowser`和`IVSMDPropertyGrid`（在 vsmanaged.h 中声明） 用于创建和填充对话框或窗口内的属性网格。  
  
 项目的体系结构已从以前版本的显著更改[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 具体而言，哪些项目的概念处于活动状态已更改。 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，没有活动的项目的概念。 在以前的开发环境中，活动的项目时的项目的生成和部署命令而不考虑上下文将默认为。 现在，解决方案控制，并且仲裁的生成和部署命令应用于哪些项目。  
  
 现在，在以下三种不同方式捕获先前活动项目：  
  
-   启动项目  
  
     你可以指定一个项目或项目从解决方案的属性页中，它将在用户按下 F5 或从生成菜单中选择运行时开始。 这适用的方式类似于在使用粗体字体其名称显示在解决方案资源管理器的意义上旧的活动项目。  
  
     可以通过调用自动化模型中的属性中检索启动项目`DTE.Solution.SolutionBuild.StartupProjects`。 在 VSPackage，你调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>方法。 `IVsSolutionBuildManager`作为由服务提供`QueryService`SID_SVsSolutionBuildManager 上。 有关详细信息，请参阅[项目配置对象](../../extensibility/internals/project-configuration-object.md)和[解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
-   活动解决方案生成配置  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]具有一个活动解决方案配置中，通过实现自动化模型中可用`DTE.Solution.SolutionBuild.ActiveConfiguration`。 解决方案配置为包含每个项目 （每个项目可以具有不同名称的多个平台有多个配置） 解决方案中的一个项目配置的集合。 与解决方案的属性页相关的详细信息，请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)。  
  
-   当前所选的项目  
  
     实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>方法来检索的项目层次结构和项目项或选择的项。 从 DTE，将使用`SelectedItems.SelectedItem.Project`和`SelectedItems.SelectedItem.ProjectItem`方法。 没有在核心中这些标题下的示例代码[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文档。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [项目配置对象](../../extensibility/internals/project-configuration-object.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)