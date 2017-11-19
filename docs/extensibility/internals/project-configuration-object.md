---
title: "项目配置对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a1b1e7c7b782868ece2c640f75fd506018f3e04
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-object"></a>项目配置对象
项目配置对象管理到 UI 的配置信息的显示。  
  
 ![Visual Studio 项目配置](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
项目配置属性页  
  
 项目配置提供程序管理的项目配置。 环境和其他包，以访问和检索有关项目的配置的信息，请调用附加到项目配置提供程序对象的接口。  
  
> [!NOTE]
>  无法创建或编辑解决方案配置文件以编程方式。 必须使用`DTE.SolutionBuilder`。 请参阅[解决方案配置](../../extensibility/internals/solution-configuration.md)有关详细信息。  
  
 若要发布要在配置 UI 中使用的显示名称，你的项目应实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>。 环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，它返回的列表`IVsCfg`可用于获取要在环境的用户界面中列出的配置和平台信息的显示名称的指针。 通过存储在活动解决方案配置的项目的配置确定的活动配置和平台。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>方法可以用于检索的活动项目配置。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>对象 （可选） 可以实现上<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>对象<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>对象可用于检索`IVsProjectCfg2`根据规范项目配置名称的对象。  
  
 另一种方法可提供项目配置的访问权的环境和其他项目的项目提供的一个实现，为`IVsCfgProvider2::GetCfgs`方法以返回一个或多个配置对象。 项目也可实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>，它继承自`IVsProjectCfg`和从而从`IVsCfg`，以提供配置特定的信息。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>添加、 删除和重命名项目配置为支持平台和功能。  
  
> [!NOTE]
>  由于 Visual Studio 不再限制为两种配置类型、 处理配置的代码应该不会写入具有假设有关多个配置，也不应它编写假设，只有一个项目配置一定是调试或零售。 这使得使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>废弃不用。  
  
 调用`QueryInterface`从返回的对象上`IVsGetCfgProvider::GetCfgProvider`检索`IVsCfgProvider2`。 如果`IVsGetCfgProvider`通过调用找不到`QueryInterface`上`IVsProject3`项目对象，你可以通过调用访问的配置提供程序对象`QueryInterface`上为返回的对象的层次结构根浏览器对象`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`，或通过指向返回的配置提供程序的指针`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`。  
  
 `IVsProjectCfg2`主要提供访问用于生成、 调试和部署管理对象，并允许到组输出自由的项目。 方法`IVsProjectCfg`和`IVsProjectCfg2`可以用来实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>来管理生成过程中，和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>配置的输出组的指针。  
  
 项目必须返回相同数量的它支持即使的组中包含的输出数可能不同配置配置的每个配置的组。 组还必须拥有相同的标识符信息 （规范名称、 显示名称和组信息） 配置配置项目中。 有关详细信息，请参阅[输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)。  
  
 若要启用调试，你的配置应实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。 `IVsDebuggableProjectCfg`是由项目以允许调试器以启动配置实现的可选接口，在配置对象上实现`IVsCfg`和`IVsProjectCfg`。 用户选择通过按 F5 启动调试器，则环境将调用它。  
  
 `ISpecifyPropertyPages`和`IDispatch`用于与属性页一起检索并向用户显示依赖于配置的信息。 有关详细信息，请参阅[属性页](../../extensibility/internals/property-pages.md)。  
  
## <a name="see-also"></a>另请参阅  
 [管理配置选项](../../extensibility/internals/managing-configuration-options.md)   
 [生成的项目配置](../../extensibility/internals/project-configuration-for-building.md)   
 [输出的项目配置](../../extensibility/internals/project-configuration-for-output.md)   
 [属性页](../../extensibility/internals/property-pages.md)   
 [解决方案配置](../../extensibility/internals/solution-configuration.md)