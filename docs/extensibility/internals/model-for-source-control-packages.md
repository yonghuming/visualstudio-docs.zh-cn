---
title: "模型表示源代码管理包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8dacc0a3dfc230085c7575960238711d16d1ef8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="model-for-source-control-packages"></a>源代码管理包的模型
以下模型表示源控件的实现的示例。 在模型中，你将看到必须实现的接口，并必须调用的环境服务。 如所有服务，你实际调用的方法的一个特定的接口，通过该服务获取。 标识的类名称以使其更轻松地了解如何执行源代码管理。  
  
 ![SCC &#95;TUP 示例](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
示例源代码管理项目  
  
## <a name="interfaces"></a>接口  
 你可以使用下表中所示的接口列表视图的 Visual Studio 中你新项目类型中实现源代码管理。  
  
|接口|使用|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|由项目和编辑器保存它们或更改 （更新） 文件前的调用。 访问此接口时使用的<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|调用项目，以便添加、 删除或重命名文件或目录的请求权限。 此接口还调用以通知环境时已批准的添加、 删除或重命名操作已完成的项目。 使用访问<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|实现的任何实体都注册项目添加、 重命名或删除文件或目录时收到通知。 若要注册事件通知，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|由项目源代码管理包中注册并获取有关源控件状态的信息。 访问此接口时使用的<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|实现对有关文件信息的源控件请求作出响应，并以获得控件设置项目文件所需的源的项目。|  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [支持源代码管理](../../extensibility/internals/supporting-source-control.md)