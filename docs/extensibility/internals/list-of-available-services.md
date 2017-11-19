---
title: "可用服务列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
caps.latest.revision: "49"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f2fca0baa747311b08983d8fc7e30efd02ae4c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="list-of-available-services"></a>可用服务列表
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和 Visual Studio SDK 支持以下服务。 某些包提供未在此处列出其自己服务 — 例如，语言服务没有单个服务 GUID。 你必须使用的语言的名称来在注册表中查找语言服务的 GUID。  
  
 使用此处列出或从某个其他源 （例如，语言服务） 中获取的服务 Guid 来获取主接口或显示与每个服务的接口。  
  
## <a name="the-services"></a>服务  
  
|服务|接口|Visual Studio|Visual Studio 2005|描述|  
|-------------|---------------|-------------------|------------------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SBindHost>|<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>|是|是|Vspackage 用于获取<xref:Microsoft.VisualStudio.OLE.Interop.IBindHost>ActiveX 控件以方便异步数据传输中的接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDTE>|<xref:EnvDTE.DTE>|No|是|获取用于自动化的设计时可扩展性 (DTE) 对象。<br /><br /> C/C + + ID: SID_SDTE|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate>|<xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate>|是|是|由用于显示控件的默认事件处理窗体设计器实现。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch>|IDispatch|是|是|使 VSPackage 来访问另一个 VSPackage 或控件的自动化接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib>|是|是|使 VSPackage 来添加或创建扩展的类型库。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SDirList>|<xref:Microsoft.VisualStudio.Shell.Interop.IDirList>|No|是|提供对容器访问权限的名为列表的列表;例如，搜索中所示的目录列表**查找和替换**中的对话框**查找中**下拉列表。 <xref:Microsoft.VisualStudio.Shell.Interop.IDirList>对象可以是从读取以及写入。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner>|是|是|使 VSPackage 能够动态显示或隐藏其自己工具窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager>|<xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager>|是|是|使 VSPackage 以指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它需要通过指定的许可证密钥列表的类。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>|是|是|使 VSPackage 来访问相对于本地注册表[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]注册表配置单元。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager>|是|是|提供组件协调服务，例如消息循环、 键盘循环和事件通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>|是|是|使 VSPackage 来访问的各种用户界面 (UI) 元素[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，如帮助、 状态栏和 UI 事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|是|是|使 VSPackage 来使用的 UI 集成其 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite>|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite>|是|是|使 VSPackage 来控制特定于工具的 UI 更改。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>|是|是|使 VSPackage 来访问容器的撤消管理器来或者参与该容器的撤消堆栈或访问该容器的撤消堆栈。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>|是|是|使 VSPackage 来提供其自身的服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib>|<xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib>|是|是|使窗体设计器中，以使类型库可供引用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>|是|是|提供对所选内容容器中的选择访问。 由窗体设计器。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher>|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|是|是|使 VSPackage 来参与命令处理程序链和处理集成的开发环境 (IDE) 或本身代表的命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale>|<xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale>|是|是|提供对 UI 区域设置信息的主机的访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>|No|是|使 VSPackage 来启用日志记录后记录高级消息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg>|是|是|提供对访问**添加项目项**对话框，允许 Vspackage 实现其自己**添加项**菜单选项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg>|是|是|显示**添加引用**对话框。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>|是|是|使 VSPackage 来确定是否提供指向 devenv.exe 的命令行开关。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser>|No|是|使 VSPackage 来创建一个新**调用浏览器**在调试时使用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView>|是|是|使 VSPackage 来同步**类视图**与特定对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping>|是|是|映射到 Guid 并返回命令名称并确定所有可用的命令和名称的名称提供支持。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView>|No|是|使 VSPackage 来操作**代码定义视图**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler>|是|是|内部服务。 请勿使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|是|是|提供对代码窗口可以包含一个或多个文档的访问。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|是|是|使 VSPackage 来将更改添加到代码窗口如下拉栏。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2>|是|是|使 VSPackage 来运行命令**命令窗口**并与之否则交互**命令窗口**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection>|No|是|使 VSPackage 来操作的列表**命令**由维护 windows [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager>|是|是|使 VSPackage 来浏览信息提供给**对象浏览器**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg>|No|是|使 VSPackage 来支持**添加引用**选项，它允许用户选择要向项目中添加的外部组件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2>|No|是|使 VSPackage 来支持**添加引用**选项，它允许用户选择要向项目中添加的外部组件。 显示之前，此版本的对话框中允许预填充的组件列表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg>|No|是|显示**Configuration Manager**对话框。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject>|No|是|使 VSPackage 来创建项目包含的其他项目集合。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol>|是|是|使 VSPackage 来更新的可调式 IDE 用于启动特定的调试引擎的协议列表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch>|是|是|使 VSPackage 来支持启动调试器。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>|是|是|使 VSPackage 来创建用于发现 Web 服务发现会话。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>|是|是|提供用于创建工厂<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>指定用于枚举的对象的层次结构 （项目）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList>|No|是|提供用于操作的其他方法**生成错误列表**任务窗口。 具体而言，使**生成错误列表**到前端的任务窗口，并强制要显示的所有错误。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager>|是|是|提供对访问**杂项文件**当前解决方案的项目节点。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>||是|是|已过时。 使用`SVsFileChangeEx`改为服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>|是|是|使 VSPackage 来访问由 IDE 触发的各种文件更改事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>|是|是|启用筛选器中显示的项到 VSPackage**添加项**对话框。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys>|是|是|使 VSPackage 来执行高级的键盘的筛选。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>|No|是|为字体提供对缓存的集的访问，并且中的颜色[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以刷新或清除特定缓存或所有缓存。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>|是|是|使 VSPackage 来操作由维护的字体和颜色设置[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 此外，此服务提供对集合的实用工具方法，用于操作字体和颜色数据访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>|是|是|提供对常规访问**输出窗口**窗格中，根据需要创建它。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem>|是|是|提供帮助系统的访问权限。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter>|是|是|使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]句柄 HTML 中以设置其输出格式的调试器。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIME>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIME>|是|是|提供访问到输入法编辑器 (IME) 从 API 中 VSPackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp>|<xref:Microsoft.VisualStudio.VSHelp.SVsHelp>|是|是|提供对访问[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]帮助系统中的关键字或 URL 访问导航控件以及通过帮助文件。 此服务是仅当帮助集成到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 和作为一个外部程序未运行。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler>|是|是|使 VSPackage 来获得对等使用鼠标滚轮单击鼠标滚轮时处理滚动和平移位图的缩放功能的访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine>|No|是|使项目层次结构节点来加载或卸载文件作为对 IntelliSense 操作支持的一部分。 加载和卸载可能会影响 IntelliSense 的项目的工具提示中显示的内容的触发器事件的过程。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost>|No|是|使项目层次结构节点提供有关嵌套 IntelliSense 项目的信息 (该实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>接口)，可以在 IntelliSense 工具提示中显示。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager>|No|是|使项目层次结构节点来建议的事件，例如在引用或配置，这可能会影响 IntelliSense 工具提示中显示的内容中的更改的侦听器。 设计用于包含语言。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>|是|是|使 VSPackage 来注册"可见"编辑器，也就是说，一个编辑器，提供完整的编辑功能，但不是对用户可见。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|是|是|使 VSPackage 来为如数据提示的文本视图和单词的范围提供附加信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>|是|是|使 VSPackage 来执行临时批处理脚本，若要执行的命令行程序，其输出发送到的输出窗格中，并分析标准警告和错误消息发送到一个错误窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory>|是|是|提供用于创建一个工厂<xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad>对象。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>|是|是|提供对链接的撤消管理器访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory>|是|是|使窗体设计器中，若要访问共享的菜单编辑器。 为查询 IVsMenuEditorFactory <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>|是|是|使 VSPackage 来创建"上下文袋"，这用于将特定的上下文的帮助关键字相关联。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser>|是|是|使 VSPackage 来导航到中的特定对象**对象浏览器**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager>|是|是|使 VSPackage 来使用其库管理器中注册[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用于管理对象，例如命名空间、 类和枚举。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch>|是|是|使 VSPackage 来搜索特定对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg>|No|是|使 VSPackage 来使用标准[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]对话框以打开项目或解决方案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>|是|是|使 VSPackage 来在常规输出窗口中创建其他输出窗格。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine>|是|是|启用的实现器<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口来分析命令行。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver>|No|是|提供一种方法来解决特定于的变量[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和嵌入到路径，以生成最终的路径。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService>|No|是|显示**预览更改**重构代码中使用的对话框。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager>|No|是|提供的访问权限的配置文件管理器[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它允许导入和导出设置数据，以及显示当前用户的配置文件设置的 UI。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI>|No|是|显示一个对话框，其中显示当前用户的配置文件设置。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame>|是|是|使 VSPackage 来重写在最初显示的属性页**属性**窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|No|是|使用 Vspackage 的通知的源控件提供程序将用于在内存中更改或保存文件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider>|No|是|使 VSPackage 项目以编程方式重写要在调试器中启动的目标。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>|是|是|使 VSPackage 来使用 IDE 中注册的编辑器工厂。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope>|No|是|使 VSPackage 来注册的搜索作用域**在文件中查找**对话框。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>|是|是|使 VSPackage 来将自身注册为高优先级命令处理程序，它允许 VSPackage 可查看所有命令。 如果根本应谨慎，使用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>|是|是|使 VSPackage 来向 IDE 注册项目类型。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager>|No|是|使 VSPackage 来从附属 Dll 加载托管和非托管资源。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView>|是|是|使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>改为服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>|是|是|提供访问到 IDE 的正在运行文档表 (RDT) 跟踪所有当前打开的文档。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|No|是|使 Vspackage 进行自我注册与源代码管理提供程序，以便他们可参与源代码管理。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|是|是|使 VSPackage 获取和设置源代码管理提供程序选项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>|No|是|提供对用户的配置文件设置的读取访问权限。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell>|是|是|使 VSPackage 来直接交互和处理其他 Vspackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger>|是|是|提供对访问[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试器。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|是|是|使 VSPackage 来访问当前选定内容和管理命令 UI 上下文。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider>|IVSMDCodeDomProvider|No|是|提供对代码文档对象模型 (DOM) 提供程序可以在本机代码中使用的访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService>|IVSMDCodeDomCreator<br /><br /> IVSMDDesignerService|No|是|托管的窗体设计器提供对 IDE 的支持访问。 `IVSMDCodeDomCreator`可以用于创建 DOM 提供程序的代码。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser>|IVSMDPropertyBrowser|No|是|提供对设计器属性 windows 服务的访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService>|No|是|提供可以返回接口的访问权限<xref:System.ComponentModel.Design.ITypeResolutionService>为本机代码中的对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope>|No|是|使您能够打开上一个程序集，并考虑锁定根据需要的作用域。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|是|是|提供到当前解决方案的顶级访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager>|是|是|使 VSPackage 与解决方案的生成过程进行交互。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>|是|是|使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>改为服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>|是|是|使 VSPackage 来存储和检索从当前解决方案.sln 文件的信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences>|No|是|提供的功能添加和更新在托管的代码程序集的引用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload>|No|是|提供对启动页的下载服务启动和停止后台线程上的下载服务的访问权限。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>|是|是|提供对 IDE 状态栏会显示访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys>|No|是|提供对用于创建具有用于签名托管的代码程序集的密码的强密钥名称和密钥文件的方法访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO>|是|是|使 VSPackage 以提供有关将数据保存在多种格式的支持。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>|是|是|提供访问 IDE 的任务列表窗口。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities>|No|是|提供用于加载和保存文本文件实用程序。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>|是|是|提供对所有的文本缓冲区，以及可在 IDE 中的隐藏的文本会话 （的隐藏区域） 的访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut>|是|是|提供的 Win32 版本`TextOut`将文本写入设备上下文 （需要 DC 句柄） 的函数。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet>|是|是|提供对文本图像或缓冲区中的文本段的列表的访问。 此服务通常在容器中实现的文档并引用当前文档。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog>|No|是|使 VSPackage 来显示一个对话框，等待在不同线程 （用于等待后台任务）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool>|No|是|使 VSPackage 来启动的后台任务，然后由维护[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>|是|是|提供对 IDE 的访问权限**工具箱**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider>|是|是|使 VSPackage 来获取信息从**工具箱**项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry>|No|是|使 VSPackage 来注册工具箱数据提供程序而不会产生预加载整个的性能成本**工具箱**。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions>|No|是|使 VSPackage 来确定如果**选项**对话框处于打开状态，并刷新所有选项页的可见性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|No|是|使 VSPackage 来监视项目的文件中的更改，并提供对源代码管理提供程序的批处理控制。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|是|是|使 VSPackage 来通知的更改可能会影响当前选定的项目项选择 IDE。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper>|是|是|使层次结构 （如项目 VSPackage） 来协调使用与其他层次结构剪贴板。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>|是|是|提供对 IDE 的 UI 元素，如工具窗口与文档窗口访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr>|是|是|使 VSPackage 若要还原的所有 windows 基于数据的流的内容的位置，或者将保存到流的所有窗口的位置。 很少使用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>|是|是|使 VSPackage 中通过多种方式打开的文档并确定谁拥有哪些文档。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>|No|是|使用的实施者<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>报告错误和信息性消息的接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService>|是|是|使 VSPackage 来创建和控制 Web 浏览会话。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites>|是|是|使 VSPackage 来将添加到用户的**收藏夹**列表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview>|是|是|使 VSPackage 来预览 Web 页，通常在子窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU>|是|是|使 VSPackage 将 URL 添加到 Url 的最近使用的 (MRU) 列表并获取 MRU 列表中的所有 Url 的列表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>|是|是|使 VSPackage 来获取包的一部分可能位于窗口框架。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService>|是|是|提供对与特定的元数据文件相关联的 XML 格式的文档文件的访问。|  
  
## <a name="see-also"></a>另请参阅  
 [COM 和托管的服务](http://msdn.microsoft.com/en-us/6c5808b4-ad87-48d7-ae06-33a81e7052af)   
 [使用并提供服务](../../extensibility/using-and-providing-services.md)