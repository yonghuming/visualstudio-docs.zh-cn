---
title: "项目模型核心组件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7759a2394f2cda19f875a85a22c4a674fee8964
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="project-model-core-components"></a>项目模型核心组件
下表来扩大项目模型。 这些表格显示接口和在该模型的接口和特定对象与关联的服务中标识的服务的简要的说明。 此外，表详细介绍在项目创建和维护，具体取决于你的特定项目类型的要求中是可选的其他接口。  
  
 有关详细信息，请参阅[支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。  
  
### <a name="package-object"></a>包对象  
  
|接口|注释|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|初始化在 IDE 中的 VSPackage 并使其服务对 IDE 可用。|  
  
### <a name="project-factory-object"></a>项目工厂对象  
  
|接口|注释|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|管理创建新的项目和打开现有项目。|  
  
### <a name="project-objects"></a>项目对象  
  
|接口|注释|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理添加和删除项目项，打开编辑器，并维护每个文档标记之间的映射和`VSITEMID`。 继承自`IVsProject`和`IVsProject2`。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理导航和显示属性并提供事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|启用命令执行类似于`IOleCommandTarget`如剪切和重命名只有当焦点位于在解决方案资源管理器应用的命令。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|用作项目层次结构的主命令目标接口。 它是用于查询其命令状态或状态和运行命令的对象的标准接口。 当你将不重点放在项目窗口时可用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|协调项目状态的持久性。 通常情况下，项目状态将存储为项目文件，但可适用于不基于文件的存储系统。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|使项目以管理其项目项，或者作为磁盘或其他存储系统中的对象上的文件的持久性的所有方面。 `IVsPeristHierarchyItem2`接口用于未实现的项<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|协调与源代码管理交互。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|使项目能够管理配置信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理项目配置对象，例如调试/发布配置。 生成、 部署和调试操作得到协调通过项目配置对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|由层次结构来控制删除 （破坏性） 或删除的层次结构项的 （非破坏性） 选项的实现。 在调用查询接口`IVsHierarchyDeleteHandler`接口从`IVsHierarchy`接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|你可以实现选择具有支持的对象`IVsCfgProvider2`上比实现的项目对象不同的 COM 标识接口`IVsHierarchy`接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|实现以使该项目可扩展由其他开发人员的可选接口。 `IVsProjectStartupServices`接口使第三方 VSPackage 来注册，以便每次你的项目加载后，您将第三方服务 GUID 加载到你的项目文件和调用保留到你的项目文件的 GUID`QueryService`对于该 GUID。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|由源层次结构中实现`UIHierarchy`窗口来协调剪贴板操作，例如剪切、 复制和粘贴。 使用`AdviseClipboardHelperEvents`接口来注册剪贴板事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|提供有关相对于其数据源拖动的项 UI 层次结构窗口中的拖放操作过程的信息。 从调用`IVsHierarchy`接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|提供有关相对于其放置目标拖动的项 UI 层次结构窗口中的拖放操作过程的信息。 从调用`IVsHierarchy`接口。|  
  
### <a name="configuration-object"></a>配置对象  
  
|接口|注释|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供有关配置信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|使项目能够管理配置信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|使项目以在调试器的控制下运行。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|实现执行其他项目的部署操作的部署项目。|  
  
### <a name="configuration-builder-object"></a>配置生成器对象  
  
|接口|注释|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理项目配置的生成操作。|  
  
### <a name="additional-project-objects"></a>其他项目对象  
  
|接口|注释|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|项中的属性显示**属性**窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|显示部署的输出。|  
  
 下表列出了在项目模型中标识的服务的简要说明。  
  
### <a name="services"></a>服务  
  
|服务|注释|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|由 Vspackage 实现项目类型以注册其项目工厂存在与 IDE。 你的 VSPackage 必须调用`QueryService`此服务并注册其项目工厂时`IVsPackage::SetSite`调用方法。 如果`SetSite`不调用方法，你的项目未实例化。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供对当前解决方案，如能够枚举项目、 创建新项目、 需要的项目进行的更改，请注意和以便在 IDE 的内部、 内置概念访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|想要参与源代码管理的项目由调用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|维护的打开的文档以确定是否已打开一个或多个项目项的表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|包含接口和方法调用时实际打开使用标准编辑器或特定编辑器的项目项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|所需这些添加、 删除或重命名其项时可调用的所有项目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理对文件或目录的更改并通知客户端时所选的文件已被更改磁盘上。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|需要由所有项目和编辑器脏项或将它们保存之前调用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理的生成和部署操作的项目配置的顺序。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供对用于大多数调试控件的低级别调试器服务的访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|启用 Vspackage 访问有关当前选择的信息，并启用与通信**属性**窗口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本与 UI 相关的 IDE 功能，例如具有创建和枚举工具窗口或文档窗口或用于错误报告给用户的能力。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供对 IDE 状态栏会显示访问。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用于实现自动化模型。 在项目模型中，将返回属性对象，允许您创建该对象的实例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用于在层次结构中的项目对象上实现剪贴板事件。 `SVsUIHierWinClipboardHelper`可以正确句柄剪切、 复制和粘贴操作。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [不在生成中： 使用 HierUtil7 项目类来实现一种项目类型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [项目模型的元素](../../extensibility/internals/elements-of-a-project-model.md)