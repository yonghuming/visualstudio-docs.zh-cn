---
title: "项目配置对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0518e4844dd7fa7710935f742bf44943a5ef945d
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-object"></a>项目配置对象
项目配置对象管理对 UI 的配置信息的显示。  
  
 ![Visual Studio 项目配置](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
项目配置属性页  
  
 项目配置提供程序管理的项目配置。 环境和其他程序包，才能访问和检索有关项目的配置的信息，请调用附加到项目的配置提供程序对象的接口。  
  
> [!NOTE]
>  无法创建或编辑解决方案配置文件以编程方式。 必须使用`DTE.SolutionBuilder`。 请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)有关详细信息。  
  
 若要发布一个显示名称来配置用户界面中使用，您的项目应实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，它返回的列表`IVsCfg`可用来获取要在环境的用户界面中列出的配置和平台的信息的显示名称的指针。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> 活动配置和平台由存储在活动解决方案配置的项目的配置决定。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>方法可以用于检索活动项目配置。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>对象都可以根据需要实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>对象<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>对象，以允许您检索`IVsProjectCfg2`根据规范项目配置名称的对象。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>  
  
 另一种方法提供对项目配置访问权限的环境和其他项目的项目提供的一个实现，为`IVsCfgProvider2::GetCfgs`方法以返回一个或多个配置对象。 项目也可能会实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>，它是从`IVsProjectCfg`，从而从`IVsCfg`，以提供特定于配置的信息。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>添加、 删除和重命名项目配置为支持平台和功能。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>  
  
> [!NOTE]
>  Visual Studio 不再限制为两种配置类型，因为处理配置的代码都不应编写使用假设多年间的配置，也不应它写入一定是一个具有只有一个配置项目的假设调试或零售。 这使得使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>已过时。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>  
  
 调用`QueryInterface`从返回的对象上`IVsGetCfgProvider::GetCfgProvider`检索`IVsCfgProvider2`。 如果`IVsGetCfgProvider`通过调用找不到`QueryInterface`上`IVsProject3`项目对象，您可以通过调用访问配置提供程序对象`QueryInterface`为返回的对象的层次结构根浏览器对象上`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`，或指向的指针为返回的配置提供程序通过`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`。  
  
 `IVsProjectCfg2`主要提供访问用于构建、 调试和部署管理对象，并允许到组输出自由的项目。 方法`IVsProjectCfg`和`IVsProjectCfg2`可以用于实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>来管理生成过程中，和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>的一种配置各输出组的指针。</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>  
  
 该项目必须返回相同数量的每个配置都支持即使包含在组中的输出数可能不同配置配置的组。 组还必须具有相同的标识符信息 （规范名称、 显示名称和组信息） 配置配置项目中。 有关详细信息，请参阅[输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)。  
  
 若要启用调试，你的配置应实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg`是由项目以允许调试器以启动配置实现的可选接口，并且在配置对象上实现`IVsCfg`和`IVsProjectCfg`。 当用户选择通过按 F5 启动调试器时，环境将调用它。  
  
 `ISpecifyPropertyPages`和`IDispatch`用属性页一起使用以检索并向用户显示依赖于配置的信息。 有关详细信息，请参阅[属性页](../../extensibility/internals/property-pages.md)。  
  
## <a name="see-also"></a>另请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)   
 [属性页](../../extensibility/internals/property-pages.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)
