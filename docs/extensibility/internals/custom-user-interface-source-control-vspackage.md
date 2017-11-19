---
title: "自定义用户界面 (源控件 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6138ffcd0c56b87e9e29a316aa2ae0ad9f982e18
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="custom-user-interface-source-control-vspackage"></a>自定义用户界面 (源控件 VSPackage)
VSPackage 通过 Visual Studio 命令表 (.vsct) 文件中声明其菜单项，则其默认状态。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 在加载 VSPackage 之前为其默认状态显示的菜单项。 随后，<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>调用方法来启用或禁用菜单项。  
  
 VSPackage 可以设置注册表项，因此可以根据命令用户界面 (UI) 上下文自动加载 VSPackage，尽管通常源代码管理 VSPackage 应加载按需而不是只需切换到特定的 UI 上下文。 有关 AutoLoadPackages 注册表项的详细信息，请参阅[管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
## <a name="vspackage-ui"></a>VSPackage UI  
 源代码管理包作为 VSPackage 实现，并不使用任何 UI。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 每个源控件 VSPackage 必须为特定的设置选项到源代码管理 VSPackage 指定其自己的 UI 元素，如菜单项、 菜单组、 工具窗口、 工具栏和任何必需的 UI。 静态还是动态，则可以启用这些 UI 元素。 静态用户界面元素在.vsct 文件中定义和是否加载 VSPackage 时，或不显示。 动态 UI 元素可能是可见具体取决于特定命令 UI 上下文，如<xref:EnvDTE.Constants.vsContextNoSolution>，或作为对的调用结果<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 动态 UI 元素的可见性符合的 Vspackage 的延迟加载的策略。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>源控件 Vspackage UI 约束  
 由于它加载后，无法从 IDE 中删除源控件 VSPackage，VSPackage 必须能够进入非活动状态。 当 VSPackage 收到通知，它不再处于活动状态时，VSPackage 禁用其 UI，并将忽略任何外部 IDE 交互。 VSPackage 的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法应隐藏命令时 VSPackage 未处于活动状态。  
  
 VSPackage 必须实现每个源代码管理`IVsSccProvider`接口。 此接口，两个方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>，VSPackage 必须实现。  
  
 VSPackage 可能已订阅了各种 IDE 事件，通过实现的源控件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>， <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>，依次类推。 此外，VSPackage 可能它们实现了注册表启用回调接口，如<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。 这些必须所有时忽略非活动状态。  
  
 以下列表显示受源代码管理 VSPackage 的活动状态的接口：  
  
-   跟踪项目文档的事件。  
  
-   解决方案的事件。  
  
-   解决方案持久性接口。 当处于非活动状态时，包不应写入.sln 和.suo 文件。  
  
-   属性扩展程序。  
  
 所需<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，且还与源代码管理关联任何可选接口将不会调用时 VSPackage 的源控件处于非活动状态。  
  
 当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 启动[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令 UI 上下文设置为当前的默认源控件 VSPackage id。 的 ID 这将导致活动的源控件显示在 IDE 中，而无实际加载 VSPackage 的 VSPackage 的静态 UI。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]vspackage，以将注册暂停[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>VSPackage 任何调用之前。  
  
 下表介绍的特定详细信息，如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 隐藏不同 UI 项。  
  
|UI 项|描述|  
|-------------|-----------------|  
|菜单和工具栏|源代码管理包必须设置的初始的菜单和工具栏可见性状态中的源控件包 id [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct 文件的部分。 这使[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 适当地设置的菜单项的状态，而无需加载 VSPackage 和调用的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。|  
|工具窗口|源代码管理 VSPackage 隐藏它拥有进行处于非活动状态时任何工具窗口。|  
|源代码管理特定于 VSPackage 的选项页|注册表项 HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts 允许 VSPackage 设置在其中需要要显示其选项页的上下文。 此项下的注册表项都通过使用服务 ID (SID) 的源控件服务并将其分配 DWORD 值 1 来创建。 每次在上下文中向注册 VSPackage 的源控件，UI 事件发生时，如果它处于活动状态，将调用 VSPackage。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [管理 VSPackages](../../extensibility/managing-vspackages.md)