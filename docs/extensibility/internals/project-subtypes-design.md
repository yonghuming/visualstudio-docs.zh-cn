---
title: "项目子类型设计 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70d16c90ad8ef4837ad9d131e46ed2027dd6c543
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-subtypes-design"></a>项目子类型设计
项目子类型让 Vspackage 扩展基于 Microsoft Build Engine (MSBuild) 项目。 使用聚合，可以重用核心管理项目系统中实现的大容量[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]但仍自定义用于特定方案的行为。  
  
 以下主题详细介绍的基本设计和实现项目子类型：  
  
-   项目子类型设计。  
  
-   多级聚合。  
  
-   支持接口。  
  
## <a name="project-subtype-design"></a>项目子类型设计  
 通过聚合主项目子类型的初始化<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>对象。 此聚合可让项目子类型以重写或增强大部分基本项目的功能。 项目子类型获取第一个机会处理属性使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>，命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>，和项目项管理使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>。 此外可以扩展项目子类型：  
  
-   项目配置对象。  
  
-   依赖于配置的对象。  
  
-   独立于配置的浏览对象。  
  
-   项目自动化对象。  
  
-   项目自动化属性集合。  
  
 通过项目子类型的扩展性的详细信息，请参阅[属性和方法扩展通过项目子类型](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)。  
  
##### <a name="policy-files"></a>策略文件  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境提供了与在其实现中的策略文件的项目子类型对基本项目系统的扩展的示例。 策略文件允许的调整[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境管理功能，包括解决方案资源管理器，**添加项目**对话框中，**添加新项**对话框中和**属性**对话框。 策略子类型重写并增强了通过这些功能<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>，`IOleCommandTarget`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>实现。  
  
##### <a name="aggregation-mechanism"></a>聚合机制  
 环境的项目子类型聚合机制支持多个级别的聚合，从而允许由进一步 flavoring 风格化的项目实现高级子类型。 此外，项目的支持的对象的子类型，如<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>，旨在允许多个级别的分层。 为了与保持一致的 COM 和 COM 的约束聚合规则、 项目子类型和基项目需要以协作方式进行编程，允许内部的子类型或基项目正确参与委派方法调用，以及管理引用计数. 也就是说，要聚合的项目必须进行编程，从而支持聚合。  
  
 下图显示多级项目子类型聚合的图示。  
  
 ![Visual Studio 多级项目风格图形](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
多级项目子类型  
  
 多级项目子类型聚合包含三个级别，按高级的项目子类型进一步聚合则按项目子类型，聚合的基本项目。 图重点介绍一些作为的一部分提供的支持接口[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]项目子类型体系结构。  
  
##### <a name="deployment-mechanisms"></a>部署机制  
 许多在基本项目系统个通过项目子类型，增强的功能是部署机制。 项目子类型通过实现配置接口影响部署机制 (如<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>)，通过调用 QueryInterface 上检索<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>。 在项目子类型和高级的项目子类型在其中添加不同的配置实现方案中，基本项目调用`QueryInterface`上的高级的项目子类型的`IUnknown`。 如果内部项目子类型包含基项目要求你的配置实现，高级的项目子类型委托给内部项目子类型由提供的实现。 作为一种机制来持久保存到另一个从一个聚合级别的状态，项目子类型的所有级别都实现<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>到项目文件保留非生成相关的 XML 数据。 有关详细信息，请参阅[MSBuild 项目文件中保留数据](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。 <xref:EnvDTE80.IInternalExtenderProvider>作为一种机制来检索自动化扩展程序从项目子类型实现。  
  
 下图重点介绍自动化扩展程序实现，项目配置浏览对象特别是，项目子类型用于扩展基本项目系统。  
  
 ![图： VS 项目风格自动扩展程序](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
项目子类型自动化扩展程序。  
  
 项目子类型可以进一步扩展通过扩展自动化对象模型的基本项目系统。 这些定义为 DTE 自动化对象的部分，用于扩展项目对象`ProjectItem`对象和`Configuration`对象。 有关详细信息，请参阅[扩展基本项目对象模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)。  
  
## <a name="multi-level-aggregation"></a>多级聚合  
 包装的较低级别的项目子类型的项目子类型实现需要以协作方式进行编程以允许内部项目子类型，才能正常工作。 编程职责列表包括：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>包装的内部的子类型的项目子类型的实现必须委托给<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>实现的内部项目子类型的两个<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>方法。  
  
-   <xref:EnvDTE80.IInternalExtenderProvider>包装项目子类型的实现必须委托给，其内部项目子类型。 具体而言，实现<xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>需要从内部项目子类型获取名称的字符串，然后再进行连接它想要将作为扩展程序添加的字符串。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>的包装项目子类型的实现必须实例化<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>其内部的对象项目子类型，然后将其保留为专用的委托，因为仅基项目的项目配置对象直接知道包装项目子类型配置对象存在。 外部项目子类型可以最初选择想要直接，处理配置接口，然后委托给内部项目子类型的实现 rest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>。  
  
## <a name="supporting-interfaces"></a>支持接口  
 基本项目调用委托给支持项目子类型，所添加的接口来扩展其实现的各个方面。 这包括扩展项目配置对象和各种属性浏览器对象。 这些接口检索通过调用`QueryInterface`上`punkOuter`(指向的指针`IUnknown`) 的最外层项目子类型聚合器。  
  
|接口|项目子类型|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|允许到的项目子类型：<br /><br /> -提供的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>。<br />-允许项目子类型，以提供其自己的实现，从而控制调试器启动<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。<br />-通过适当地处理禁用设计时表达式计算`DBGLAUNCH_DesignTimeExprEval`情况下，在其实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>。|  
|<xref:EnvDTE80.IInternalExtenderProvider>|允许到的项目子类型：<br /><br /> 扩展<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>的项目以添加或删除配置项目的独立属性。<br />扩展项目自动化对象 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) 的项目。<br /><br /> 上面的属性值，将从<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>枚举。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|允许项目子类型，将映射回<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>给定项目配置浏览对象的对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|允许项目子类型，将映射回<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>或`VSITEMID`给定项目配置浏览对象的对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|允许项目子类型，以任意结构化的 XML 将数据保存到项目文件 （.vbproj 或.csproj）。 此数据不是对 MSBuild 可见的。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|允许到的项目子类型：<br /><br /> -添加新的 MSBuild 属性要保留。<br />-MSBuild 中删除不必要的属性。<br />MSBuild 属性的当前值查询。<br />-更改 MSBuild 属性的当前值。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>