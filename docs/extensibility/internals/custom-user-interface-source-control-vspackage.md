---
title: "自定义用户界面 (源控制 VSPackage) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
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
ms.openlocfilehash: 0d4940ea62ac65671ffcb3bb29958e3d2e544c09
ms.lasthandoff: 02/22/2017

---
# <a name="custom-user-interface-source-control-vspackage"></a>自定义用户界面 (源控制 VSPackage)
VSPackage 通过 Visual Studio 命令表 (.vsct) 文件中声明其菜单项，则其默认状态。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 在加载 VSPackage 之前为其默认状态显示的菜单项。 随后，<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>调用方法来启用或禁用菜单项。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 VSPackage 可以设置一个注册表项，以便可以根据命令用户界面 (UI) 上下文自动加载 VSPackage，尽管通常的源控件按需而不是只需切换到特定 UI 上下文应该加载 VSPackage。 有关 AutoLoadPackages 注册表项的详细信息，请参阅[管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
## <a name="vspackage-ui"></a>VSPackage UI  
 源代码管理包作为 VSPackage 实现，并且不使用任何 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 有关选项的特定设置到源代码管理 VSPackage，VSPackage 的每个源控件必须指定其自己的 UI 元素，如菜单项、 菜单组、 工具窗口、 工具栏和任何必需的 UI。 静态或动态，则可以启用这些 UI 元素。 静态的用户界面元素在.vsct 文件中定义并是否加载 VSPackage 时，或不显示。 动态 UI 元素可能会看到具体取决于特定命令 UI 上下文中，如<xref:EnvDTE.Constants.vsContextNoSolution>，或作为对的调用结果<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:EnvDTE.Constants.vsContextNoSolution> 动态 UI 元素的可见性都遵循延迟加载 Vspackage 的策略。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>源控件 Vspackage UI 约束  
 加载后，源代码管理 VSPackage 无法从 IDE 中删除，因为 VSPackage 必须能进入非活动状态。 VSPackage 接收通知，它不再处于活动状态时，VSPackage 禁用其 UI，并将忽略任何外部 IDE 交互。 VSPackage 的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法应在 VSPackage 未处于活动状态时隐藏命令。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 每个源控件必须实现 VSPackage`IVsSccProvider`接口。 该接口上的两种方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>，必须实现的 VSPackage。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>  
  
 VSPackage 可能已由实现的各种 IDE 事件订阅的源控件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>， <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>，依次类推。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 此外，VSPackage 可能未能实现注册表启用回调接口，如<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 这些必须全部时，忽略非活动状态。  
  
 以下列表显示受源代码管理 VSPackage 的活动状态的接口︰  
  
-   跟踪项目文档的事件。  
  
-   解决方案的事件。  
  
-   解决方案持久性接口。 当非活动状态时，包不能写入.sln 和.suo 文件。  
  
-   属性扩展程序。  
  
 所需<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，并且还与源代码管理关联的任何可选接口时，不调用 VSPackage 的源控件处于非活动状态。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
  
 当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 启动时，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]将命令 UI 上下文设置为当前默认的源代码管理 VSPackage id。 ID 这会导致活动的源控件才会显示在 IDE 中而不实际加载 VSPackage 的 VSPackage 的静态 UI。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]暂停的 VSPackage 中注册[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>VSPackage 任何调用之前。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>  
  
 下表描述的特定详细信息，如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不同 UI 项目，IDE 将隐藏。  
  
|用户界面项|说明|  
|-------------|-----------------|  
|菜单和工具栏|源代码管理包必须将初始菜单和工具栏的可见性状态设置为中的源控制包 ID [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct 文件的部分。 这使[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 以适当地设置菜单项的状态，而无需加载 VSPackage 和调用的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>|  
|工具窗口|源代码管理 VSPackage 隐藏进行非活动状态时它所拥有任何工具窗口。|  
|源代码管理 VSPackage 特定选项页|注册表项 HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts，可以设置在其中需要要显示其选项页的上下文的 VSPackage。 通过使用服务的源代码管理服务的 ID (SID) 并将其分配 DWORD 值 1 创建者必须在此项下的注册表项。 每次在上下文中注册 VSPackage 的源控件，UI 事件发生时，如果处于活动状态，将调用 VSPackage。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution></xref:EnvDTE.Constants.vsContextNoSolution>   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)
