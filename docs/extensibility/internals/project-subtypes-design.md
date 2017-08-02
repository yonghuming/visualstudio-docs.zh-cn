---
title: "项目的子类型设计 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目子类型设计"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# 项目的子类型设计
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目子类型允许 Vspackage 扩展基于 Microsoft Build Engine \(msbuild\) 的项目\)。  使用摘要可以重用在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 实现的核心托管项目系统的大部分，仍自定义特定方案的行为。  
  
 以下主题详细介绍项目子类型的基本设计和实现:  
  
-   项目子类型模型。  
  
-   多个摘要。  
  
-   支持接口。  
  
## 项目子类型模型  
 项目子类型的初始化通过聚合主 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 对象实现。  此摘要使项目子类型重写或增强大多数该基项目的功能。  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>，使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>，项目子类型获取第一个机会处理属性，命令和项目项管理。  项目子类型也可以扩展:  
  
-   项目配置对象。  
  
-   配置相关对象。  
  
-   配置独立浏览对象。  
  
-   项目自动化对象。  
  
-   项目自动化属性集合。  
  
 有关项目子类型的扩展性的更多信息，请参见 [属性和扩展项目的子类型的方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)。  
  
##### 策略文件  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 环境提供扩展基项目系统的示例与其策略文件的实现项目的子类型。  策略文件允许建模 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 环境通过管理包含解决方案资源管理器、 **添加项目** 对话框、 **添加新项目** 对话框和 **属性** 对话框的函数。  策略子类型通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>、 `IOleCommandTarget` 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 实现重写并引发这些功能。  
  
##### 聚合结构  
 环境的项目子类型聚合结构支持多个聚合级别，从而允许高级子类型由进一步调味料实现一个调味的项目。  此外，项目子类型支持的对象，例如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>，旨在帮助层的多个级别。  追赶 COM 和 COM 摘要约束规则，项目子类型和基项目需要公共地编制实现内部子类型或正确参与的基项目委托的方法调用，并管理引用计数。  即将聚合的项目必须设计支持聚合。  
  
 下图显示多个项目子类型总结的一个图示。  
  
 ![图：Visual Studio 多级项目风格](~/docs/extensibility/internals/media/vs_multilevelprojectflavor.gif "VS\_MultilevelProjectFlavor")  
多个项目子类型  
  
 多个项目子类型摘要中三个级别，基本项目，由项目子类型聚合，然后进一步复合由高级项目子类型。  该图重点介绍提供作为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 项目子类型体系结构的节中的某些支持的接口。  
  
##### 部署机制  
 在项目子类型引发的许多基本项目系统功能中为部署机制。  项目子类型通过实现通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>的 QI 检索的配置界面影响部署机制 \(如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>\)。  在项目子类型和高级项目子类型添加不同的配置实现的方案，基项目对高级项目子类型的 `IUnknown`的 `QueryInterface` 。  如果内部项子类型包含基项目请求的配置实现，高级项目子类型委托给内部项子类型提供的实现。  保留的结构从一个摘要级别状态到另一个项目，子类型的所有级别实现 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 保持非编译相关的 XML 数据加载到项目文件。  有关更多信息，请参见 [MSBuild 项目文件中保存数据](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。  <xref:EnvDTE80.IInternalExtenderProvider> 实现为结构与项目子类型检索自动化扩展程序。  
  
 下图介绍自动化扩展程序实现，项目配置特别是浏览对象，用于使项目子类型扩展了基本项目系统。  
  
 ![图：VS 项目风格自动扩展程序](~/docs/extensibility/internals/media/vs_projectflavorautoextender.gif "VS\_ProjectFlavorAutoExtender")  
项目子类型自动化扩展程序。  
  
 项目子类型可以通过扩展自动化对象模型进一步扩展基本项目系统。  这些定义，对自动化对象的部件和用于扩展项目 `ProjectItem` 对象、对象和 `Configuration` 对象。  有关更多信息，请参见[扩展的对象模型的基本项目](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)。  
  
## 多个摘要  
 包装底部项目子类型的项子类型实现所需公共地编制允许内部项子类型正常工作。  编程的职责列表包括:  
  
-   包装内部子类型项目子类型的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 实现必须委托给 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 内部项子类型的实现 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> 方法的。  
  
-   包装项目子类型的 <xref:EnvDTE80.IInternalExtenderProvider> 实现必须委托为其内部项的子类型。  具体而言， <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> 的实现需要获取字符串名称从需要添加为扩展程序的内部项子类型的然后连接字符串。  
  
-   包装项目子类型的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> 实现必须实例化其内部项子类型 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> 对象和保存它作为私有委托，，因为只有基本项目的项目配置对象直接了解包装项目子类型配置对象存在。  它直接希望处理的外部项的子类型可以选择最初配置接口，然后将其他到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>的内部项子类型的实现。  
  
## 支持接口  
 基项目委托调用支持项目子类型添加的接口，扩展其实现的各个方面。  这包括扩展的项目配置对象和各个属性浏览器对象。  这些接口通过调用 `punkOuter` \(可 `IUnknown`的指针的 `QueryInterface` 检索\) 最外面的项目子类型聚合函数。  
  
|接口|项目子类型|  
|--------|-----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|向项目子类型:<br /><br /> -   提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 的实现。<br />-   通过允许项子类型提供其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>的实现控件调试器的生成。<br />-   通过适当地处理在其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>的实现的 `DBGLAUNCH_DesignTimeExprEval` 用例禁用设计时表达式计算。|  
|<xref:EnvDTE80.IInternalExtenderProvider>|向项目子类型:<br /><br /> -   扩展该项的 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 添加或移除该项的独立于配置的属性。<br />-   扩展项目自动化对象 \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\) 该项目。<br /><br /> 上面的属性值从 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 枚举中采用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|向项目子类型映射回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> 给定对象的项目配置浏览对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|向项目子类型映射回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 或 `VSITEMID` 对象命名项目配置浏览对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|向项目子类型保存任意 XML 结构化数据到项目文件 \(.csproj 或 .vbproj\)。  此数据不可见到 MSBuild。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|向项目子类型:<br /><br /> -   添加将保留的新 MSBuild 属性。<br />-   从 MSBuild 移除不必要的属性。<br />-   MSBuild 某个属性的当前值的查询。<br />-   更改 MSBuild 属性的当前值。|  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>