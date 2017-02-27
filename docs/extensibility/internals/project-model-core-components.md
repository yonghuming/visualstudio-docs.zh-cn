---
title: "项目模型核心组件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目模型、 对象和接口"
  - "项目模型中服务"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 项目模型核心组件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下表列出了项目模型展开。  接口的表当前简要说明在设计和服务标识的和接口和服务与给定对象关联的。  此外，表详细说明是可选的项目中创建和维护基于特定项目类型的要求的其他接口。  
  
 有关更多信息，请参见 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。  
  
### 包对象  
  
|接口|注释|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|初始化 IDE 中的 VSPackage 并且其服务可供 IDE。|  
  
### 项目工厂对象  
  
|接口|注释|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|创建新项目并打开现有项目的管理。|  
  
### 项目对象  
  
|接口|注释|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理项目项添加和删除，打开编辑器，并维护映射在每个之间文档标记和 `VSITEMID`。  从 `IVsProject` 和 `IVsProject2`继承。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理导航和显示属性并提供事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|启用命令执行类似于应用的命令 `IOleCommandTarget` \(如剪切和重命名，仅当焦点在解决方案资源管理器中。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|作为主命令目标接口用作项目层次结构。  它是查询对象它们的命令状态或状态和运行的命令标准接口。  可用，当您在项目窗口中居中。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|协调项状态的持续时间。  通常，存储项状态，则项目文件，但可适应并不基于文件的存储系统。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|使该项目管理持久性的所有方面其项目项，为磁盘或对象上的文件在任何其他存储系统。  `IVsPeristHierarchyItem2` 接口为没有实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 接口的项目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|与源代码管理的交互。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|使项目管理配置信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理项目配置对象，例如调试\/发布。  生成，部署，并且调试操作将项目配置对象的协调。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|实现由层次结构控件中删除破坏性 \(\) 或 cancel \(层次结构项目的非破坏性的\) 选项。  调用 `IVsHierarchyDeleteHandler` 接口的查询接口从 `IVsHierarchy` 接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|提供实现选项具有与项目对象支持在不同的 COM 标识的 `IVsCfgProvider2` 接口实现 `IVsHierarchy` 接口的对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|其他开发人员实现使项目可扩展可选接口。  `IVsProjectStartupServices` 接口允许第三方 VSPackage 注册 GUID 您保存到项目文件，以便该项目每次加载，可以加载第三方服务 GUID 到项目文件并调用该 GUID 的 `QueryService` 。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|实现由 `UIHierarchy` 窗口的源层次结构协调剪贴板操作 \(如剪切、复制和粘贴。  使用 `AdviseClipboardHelperEvents` 接口注册剪贴板操作。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|提供有关已拖动项的信息相对于其数据源在 UI 层次结构 " 窗口中的拖放操作过程。  调用从 `IVsHierarchy` 接口。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|提供有关已拖动项的信息相对于其放置目标在 UI 层次结构 " 窗口中的拖放操作过程。  调用从 `IVsHierarchy` 接口。|  
  
### 配置对象  
  
|接口|注释|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供有关配置的信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|使项目管理配置信息。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|使项目运行受调试器的控件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|实现由执行其他项目的部署操作的部署项目。|  
  
### 配置生成器对象  
  
|接口|注释|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理项目配置的生成操作。|  
  
### 其他项对象  
  
|接口|注释|  
|--------|--------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|显示在 **属性** 窗口中的项属性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|显示部署的输出。|  
  
 下表显示在项目模型标识的服务的简要说明。  
  
### 服务  
  
|服务|注释|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|使用实现项类型注册的 Vspackage 它们的项目工厂存在与 IDE。  ，当 `IVsPackage::SetSite` 调用方法时， VSPackage 必须调用此服务和注册的 `QueryService` 其项目工厂。  如果 `SetSite` 方法未调用，则该项目不实例化。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供对内部的 IDE'S，当前解决方案中的内置概念，例如能够枚举项，创建新项目，请注意到项目更改，依此类推。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|调用希望参与源代码管理的项目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|维护表打开文档确定是否已打开一个或多个项目项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|使用标准编辑或为特定编辑器，包含一个名为的接口和方法实际上打开项目项。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|必须由所有项调用时，它们会增加时，请移除或将其重命名项目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|，当所选的文件在磁盘上时，都发生了更改管理对文件或目录的更改并通知客户端。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|必须由所有项目和编辑调用，这些错误的项目或保存它们。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理生成和部署操作序列项目配置的。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供对用于大多数调试控件的低级调试器服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|启用对信息的 Vspackage 获取有关当前选择并启用与 **属性** 窗口的通信。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本与用户界面相关的 IDE 功能，例如能够创建和枚举工具窗口或文档窗口或错误用户报告。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供对 IDE 的状态栏。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用于实现自动化模型。  在项目模型，则将返回允许您创建该对象实例的属性对象。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用于实现在项对象的剪贴板操作在层次结构。  `SVsUIHierWinClipboardHelper` 正确可以处理剪切、复制和粘贴操作。|  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/zh-cn/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [项目模型的元素](../../extensibility/internals/elements-of-a-project-model.md)