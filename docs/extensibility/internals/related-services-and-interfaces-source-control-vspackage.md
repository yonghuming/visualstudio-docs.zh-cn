---
title: "相关的服务和接口 (源控件 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d652db21fb98cbb0f06c2ac5ceec0f8f239beff6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相关的服务和接口 (源控件 VSPackage)
本部分列出了所有的源控件中的 VSPackage 相关接口[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。 源代码管理 VSPackage 实现某些这些接口，并使用其他完成源代码管理任务。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>接口由和版本的源控件 Vspackage 实现  
 以下接口中所述[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，和源代码管理 VSPackage 实现它们的具体取决于其所需的功能集的一个子集。 某些接口来标记作为所需，然后由每个源的控件 VSPackage 必须实现。  
  
 包未实现，这些接口[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的默认实现。 请注意即在搜索条件时注册没有 VSPackage 和不控制任何项目，默认实现专用于这种情况。 正确编写的源代码 VSPackage 实现所有必要的接口，而不是无需留给这些接口的默认实现。  
  
 源代码管理 VSPackage 必须实现封装部分或全部以下接口一个专用服务。  
  
 接口是：  
  
-   必需的： 相应的实体 （源代码管理 VSPackage，源存根 （stub），项目） 必须实现的接口。  
  
-   建议： 实体应实现此接口;否则，源代码管理功能可能受到限制。  
  
-   可选： 实体可以实现此接口可提供更丰富的功能集。  
  
|接口|用途|由实现|实现？|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|编辑器调用此接口，然后再修改或保存文件。 VSPackage 可以签出该文件或拒绝该操作，如果签出失败的源代码管理。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|此接口提供基本源代码管理功能，对于项目，如注册和注销与源代码管理项目和基本源控件中绘制标志符号提供支持。|源代码管理 VSPackage|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|此接口从获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>使用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>函数，或通过只需强制转换为对象实现`IVsHierarchy`到`IVsSccProject2`。 它用于获取的项目中的源控件下的文件或用于通知的当前源代码管理状态或位置中的项目。|Project|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|集成模块使用此接口设置当前活动的 VSPackage。|源代码管理 VSPackage|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|此接口基于订阅模型。 任何 VSPackage 可以指示它想要接收文档事件以及建议 shell，即将出现的事件。 实现和由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，后者反过来将传递事件实现`IVsTrackProjectDocumentsEvents2`到 VSPackage。|源存根 （stub)|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|此接口提供了批处理、 同步的读/写操作和一个高级`OnQueryAddFiles`方法。|源存根 （stub)|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**解决方案资源管理器**和项目到项目中，添加新文件时或在重命名或从项目中删除文件和文件夹时调用此接口。 源代码管理 VSPackage 可以签出项目文件，或取消该操作。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**解决方案资源管理器**和项目调用以响应对 IVstrackProjectDocuments3 接口的方法所做的调用此接口。 VSPackage 可以跟踪批处理的操作，同步的源控件读/写操作，并使用更高级`OnQueryAddFiles`方法。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|此接口提供登记管理支持 Web 项目。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|此接口用于检索项目受源代码管理文件的工具提示。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|此接口提供扩展的命名空间支持。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage 使用此接口将集成到一个命名空间扩展**新建**，**打开**，或**保存**对话框。 因此，项目可以自动添加到源代码管理，在创建，或添加到源代码管理时保存操作是否生效。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage 使用此接口来定义其他标志符号，为源控件中的节点的标志符号**解决方案资源管理器**。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**添加**Web 项目的对话框中使用此接口。 它提供用于浏览源代码管理位置以及打开 Web 项目以前在该位置的源控件存储库中添加方法。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|此接口提供从源代码管理项目的异步 （后台） 加载的支持。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|此接口允许项目以查看由启动异步加载的进度<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>。|Project|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|此接口允许 IDE 以在活动的源控件 VSPackage 中查询。 IDE 查询具有的含义，即使没有注册 VSPackage 的活动的源控件的源代码管理设置的值。 此接口是实现，由处理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|源存根 （stub)|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|此接口用于注册 VSPackage 的源控件。|源存根 （stub)|必需|  
|<xref:EnvDTE.SourceControl>|在自动化中使用此接口。 在这种情况下，它公开可以而不显示任何 UI 执行的函数。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|使用此接口来将源控件设置保存在解决方案 (.sln) 文件。 设置包括的源控件位置和源控件状态标志。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|使用此接口来在解决方案选项 (.suo) 文件保存源代码管理设置。 这可能包括特定于用户的源代码管理设置，例如当前用户的登记位置。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|此接口用于执行操作，例如签入之前关闭解决方案，或从源代码管理中获取新的文件，打开一个项目时的项目文件以便监视事件。|源代码管理 VSPackage|建议|  
  
## <a name="see-also"></a>另请参阅  
 [设计元素](../../extensibility/internals/source-control-vspackage-design-elements.md)