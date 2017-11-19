---
title: "源控件配置详细信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17e14d4f8d3d62297ae1d2f3e62a9ed0574fef9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-configuration-details"></a>源控件配置详细信息
若要实现源代码管理，你需要以正确配置你的项目系统或编辑器执行以下操作：  
  
-   请求转换为已更改状态的权限  
  
-   请求权限来保存文件  
  
-   请求添加、 删除或重命名项目中的文件的权限  
  
## <a name="request-permission-to-transition-to-changed-state"></a>请求转换为已更改状态的权限  
 项目或编辑器必须请求转换为已更改 （更新） 状态的权限，通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>。 实现每个编辑器<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>必须调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和接收的批准才能在返回之前从环境中更改该文档`True`为`M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`。 项目是实质上是项目文件中，编辑器中，因此，具有相同负责实现项目文件的更改状态跟踪，文本编辑器一样对其文件。 环境处理的解决方案，已更改的状态，但你必须处理的任何对象解决方案引用，但不会存储，如项目文件或其项已更改的状态。 一般情况下，如果你的项目或编辑器不负责管理工作项的持久性，然后它负责实现更改状态跟踪。  
  
 以响应`IVsQueryEditQuerySave2::QueryEditFiles`调用，该环境可以执行以下操作：  
  
-   拒绝调用以更改，在这种情况下的编辑器或项目必须保持不变 （干净） 状态。  
  
-   指示文档数据应重新加载。 对于项目，环境将重新加载项目的数据。 编辑器必须重新加载的数据从磁盘通过其<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>实现。 在任一情况下，重新加载数据时，可以更改在项目或编辑器中的上下文。  
  
 它是一种复杂且难以实现的任务翻新相应`IVsQueryEditQuerySave2::QueryEditFiles`到现有基本代码的调用。 因此，应将这些调用集成项目或编辑器的创建过程。  
  
## <a name="request-permission-to-save-a-file"></a>请求权限来保存文件  
 项目或编辑器在保存文件之前，它必须调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。 对于项目文件，这些调用自动完成的解决方案，知道何时保存项目文件。 编辑器的负责进行这些调用，除非的编辑器实现`IVsPersistDocData2`使用 helper 函数<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>。 如果你的编辑器实现`IVsPersistDocData2`在这种方式，则调用`IVsQueryEditQuerySave2::QuerySaveFile`或`IVsQueryEditQuerySave2::QuerySaveFiles`为你进行。  
  
> [!NOTE]
>  始终提前进行这些调用 — 即，当你的编辑器是能够接收取消一次。  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>请求添加、 删除或重命名项目中的文件的权限  
 一个项目可以添加、 重命名或删除文件或目录之前，必须调用相应`IVsTrackProjectDocuments2::OnQuery*`以请求权限从环境的方法。 如果授予权限，则项目必须完成此操作，然后调用相应`IVsTrackProjectDocuments2::OnAfter*`方法通知环境的操作已完成。 项目必须调用的方法的<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>所有文件 （例如，特殊文件） 和而不仅仅是父文件的接口。 文件调用是必需的但目录调用都是可选的。 如果你的项目具有目录信息，则应调用相应<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法，但如果它不具有此信息，则环境将推断目录信息。  
  
 项目不应调用的方法`IVsTrackProjectDocuments2`项目在打开或关闭。 想要在启动此信息的侦听器可以等待<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>事件，并循环访问解决方案，以查找所需的信息。 在关机时，不需要此信息。 `IVsTrackProjectDocuments2`提供从<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>。  
  
 对于每个添加、 重命名和删除操作，没有`OnQuery*`方法和`OnAfter*`方法。 调用`OnQuery*`方法请求权限，若要添加，重命名或删除文件或目录。 调用`OnAfter*`方法后的文件或目录已添加、 重命名或删除的项目状态反映此新状态。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [支持源代码管理](../../extensibility/internals/supporting-source-control.md)