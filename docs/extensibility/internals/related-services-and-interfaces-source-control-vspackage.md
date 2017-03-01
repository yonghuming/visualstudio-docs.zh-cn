---
title: "相关的服务和接口 (源控制 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
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
ms.openlocfilehash: 6d16e8eb229cd5187ae91630d9330a0e0f24eda2
ms.lasthandoff: 02/22/2017

---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相关的服务和接口 (源控制 VSPackage)
本部分列出了所有的源控件中的 VSPackage 相关接口[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。 源代码管理 VSPackage 实现一些这些接口，并使用其他人来完成源代码管理任务。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>由和源控件 Vspackage 的实现的接口  
 中描述了以下接口[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，和源控件 VSPackage 实现它们的具体取决于其所需的功能集的一个子集。 一些接口来标记并由 VSPackage 的每个源控件必须实现。  
  
 包未实现时，这些接口[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的默认实现。 请注意不注册任何 VSPackage 和不控制任何项目时的默认实现设计为用例。 正确编写的源代码 VSPackage 实现所有必要的接口，而不是留给那些接口的默认实现。  
  
 VSPackage 的源控件必须实现封装部分或全部以下接口的专用服务。  
  
 接口是︰  
  
-   必需的︰ 相应的实体 (源代码管理 VSPackage，源存根 （stub），project) 必须实现的接口。  
  
-   建议︰ 实体应实现此接口;否则，源代码管理功能可能会限制。  
  
-   可选︰ 实体可以实现此接口，以提供更丰富的功能集。  
  
|接口|用途|实现者|实施？|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|编辑器调用此接口，然后再修改或保存文件。 VSPackage 可以签出该文件或拒绝该操作，如果签出失败的源代码管理。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|此接口提供基本的源代码管理功能，对于项目，如注册和注销与源代码管理项目以及基本的源控件中绘制标志符号提供支持。|源代码管理 VSPackage|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|此接口从获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>使用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>函数，或通过简单地强制转换对象实现`IVsHierarchy`到`IVsSccProject2`。</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 它用于获取项目中的源代码管理下的文件或通知的当前源代码管理状态或位置中的项目。|Project|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|集成模块使用此接口来设置当前活动的 VSPackage。|源代码管理 VSPackage|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|此接口基于订阅模型。 任何 VSPackage，可以发出它想要接收文档事件以及可以外壳中收到通知，即将出现的事件。 实现并由处理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，后者反过来传递事件实现`IVsTrackProjectDocumentsEvents2`到 VSPackage。|源存根 （stub)|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|此接口提供批处理、 同步的读/写操作和一个高级`OnQueryAddFiles`方法。|源存根 （stub)|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**解决方案资源管理器**和新文件添加到项目，或者重命名或从项目中删除文件和文件夹时，项目会调用此接口。 源代码管理 VSPackage 可以签出项目文件，或取消该操作。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**解决方案资源管理器**和项目调用此接口以响应对 IVstrackProjectDocuments3 接口的方法进行调用。 VSPackage 可以跟踪批处理的操作，同步的源控件读/写操作，并使用更多高级`OnQueryAddFiles`方法。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|此接口提供对 Web 项目登记管理支持。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|此接口用于检索工具提示中的项目受源代码管理文件。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|此接口提供命名空间扩展支持。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage 使用此接口将集成到一个命名空间扩展**新建**，**打开**，或**保存**对话框。 因此，项目可自动添加到源代码管理，在创建过程中，或添加到源代码管理时保存操作将生效。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage 使用此接口为源控件中的节点的标志符号定义其他标志符号**解决方案资源管理器**。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**添加**Web 项目的对话框中使用此接口。 它提供用于浏览源代码管理位置以及用于打开以前在该位置的源控件存储库中添加一个 Web 项目的方法。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|此接口为异步 （后台） 加载的项目从源代码管理提供支持。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|此接口允许项目以查看由<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>启动的异步加载的进度|Project|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|此接口允许 IDE 以在活动的源控件 VSPackage 中查询。 IDE 查询有意义，即使没有注册 VSPackage 的活动的源控件的源代码管理设置的值。 此接口实现，并由处理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|源存根 （stub)|必需|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|此接口用于注册源代码管理 VSPackage。|源存根 （stub)|必需|  
|<xref:EnvDTE.SourceControl></xref:EnvDTE.SourceControl>|在自动化中使用此接口。 在这种情况下，它公开可以不显示任何 UI 的情况下执行的函数。|源代码管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|此接口用于将源控制设置保存在解决方案 (.sln) 文件。 设置包括源代码管理位置和源控件状态标志。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|此接口用于保存解决方案选项 (.suo) 文件中的源代码管理设置。 这可能包括特定于用户的源代码管理设置，如当前用户的登记位置。|源代码管理 VSPackage|建议|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|此接口用于监视的事件以执行操作，如签入之前关闭的解决方案，或从源代码管理中获取新的文件，打开项目时的项目文件。|源代码管理 VSPackage|建议|  
  
## <a name="see-also"></a>另请参阅  
 [设计元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
