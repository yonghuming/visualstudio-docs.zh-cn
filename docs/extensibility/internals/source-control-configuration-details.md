---
title: "源控件配置详细信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理 [Visual Studio SDK]，配置的详细信息"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 源控件配置详细信息
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

为了实现源控件，您需要正确配置项目系统或编辑执行以下操作:  
  
-   为转换的请求权限与更改的状态  
  
-   请求权限保存文件  
  
-   请求权限，添加、删除或重命名该项目中重命名文件  
  
## 为转换的请求权限与更改的状态  
 项或编辑必须请求权限来具有更改 \(" 更新 "\) 的状态的转换通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>。  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 的各个编辑器必须调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 和获取审批从该环境更改文档在返回 `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`的 `True` 之前。  项目实质上是项目文件的一个编辑器，结果，因此，使用实现跟踪对于项目文件的更改状态的相同的职责，文本编辑器对其执行文件。  环境处理解决方案中已更改的状态，但是，必须处理解决方案引用，但不存储任何对象的已更改的状态，与项目文件或其项目。  通常，因此，如果一个项目或编辑到托管项目，则的持久性负责实现更改状态跟踪负责。  
  
 响应 `IVsQueryEditQuerySave2::QueryEditFiles` 请调用，则该环境中执行以下操作:  
  
-   拒绝调用更改，因此，在可编辑或项目中未更改的 \(目标\) 的情况下状态必须保留。  
  
-   指示应重新加载文档数据。  对于项目，环境将重新加载数据。该项目。  编辑器必须通过其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 实现重新加载数据从磁盘。  在任何情况下，，当数据重新加载时，该项目的上下文或可编辑更改。  
  
 它是复杂的，并且诸如更新相应的 `IVsQueryEditQuerySave2::QueryEditFiles` 对现有基本代码上。  因此，这些调用应集成在一个项目或编辑的创建过程。  
  
## 请求权限保存文件  
 在项目或编辑之前保存文件，它必须调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。  对于项目文件，这些调用解决方案将自动完成，知道何时保存项目文件。  ，除非 `IVsPersistDocData2` 的编辑器实现使用 helper 函数 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>，编辑器对进行这些负责调用。  如果编辑器上述实现 `IVsPersistDocData2` ，则为 `IVsQueryEditQuerySave2::QuerySaveFile` 或 `IVsQueryEditQuerySave2::QuerySaveFiles` 的电话为您调用。  
  
> [!NOTE]
>  始终进行这些调用抢先式是，那么，当编辑器可以接收取消时间。  
  
## 请求权限，添加、删除或重命名项目中重命名文件  
 在项目可以添加，将或移除文件或目录名之前，必须调用相应的 `IVsTrackProjectDocuments2::OnQuery*` 方法请求从该环境的权限。  如果允许，则该项目必须完成操作然后调用相应的 `IVsTrackProjectDocuments2::OnAfter*` 方法通知该环境操作完成。  该项目必须调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 接口的方法所有文件 \(例如，专用文件\) 而不仅仅是父文件的。  文件名为是必须的，因此，但内容调用是可选的。  如果项目包含内容信息，则它应调用适当的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 方法，即，但是，如果它没有此信息，则环境将推断出目录信息。  
  
 该项不应调用 `IVsTrackProjectDocuments2` 方法在项目打开或关闭。  需要此信息在启动时所需的侦听器可以等待 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 事件并将该解决方案重复查找信息。  在关闭，此信息不是必需的。  `IVsTrackProjectDocuments2` 从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>提供。  
  
 对于每个添加，对，并移除事件重命名，具有 `OnQuery*` 方法和 `OnAfter*` 方法。  调用 `OnQuery*` 方法请求权限，将添加或移除文件或目录重命名为。  在文件后调用 `OnAfter*` 方法或目录已添加，重命名，或者移除和项目状态以反映新状态。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [支持的源控件](../../extensibility/internals/supporting-source-control.md)