---
title: "选择上下文对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
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
ms.openlocfilehash: 3fa5093ee38c364a4766160f8642755bc0b2a23f
ms.lasthandoff: 02/22/2017

---
# <a name="selection-context-objects"></a>选择上下文对象
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 使用全局选择上下文对象来确定在 IDE 中应显示的内容。 在 IDE 中的每个窗口可以有其自己的选择上下文对象推送到全球的选定内容上下文。 IDE 将在该窗口具有焦点时使用一个窗口中的值更新全局选定内容上下文。 有关详细信息，请参阅[用户到反馈](../../extensibility/internals/feedback-to-the-user.md)。  
  
 每个窗口框架或在 IDE 中的站点有一个名为<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服务 由你放置在该窗口框架的 VSPackage 创建的对象必须调用`QueryService`方法以获取一个指向<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>接口。</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>  
  
 框架窗口可以保留部分从可能会传播到全局选择上下文将在启动时其所选内容上下文信息。 此功能非常有用的工具窗口可能具有以开头的空选择。  
  
 修改 Vspackage 可以监视全局选择上下文触发器事件。 Vspackage 可以执行以下任务通过实施`IVsTrackSelectionEx`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>接口︰</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
-   更新层次结构中当前处于活动状态的文件。  
  
-   监视器更改为某些类型的元素。 例如，如果你的 VSPackage 使用一种特殊**属性**窗口中，您可以监视活动中的更改**属性**窗口，然后重新启动您在需要时。  
  
 按以下顺序显示了典型的过程中跟踪所选内容。  
  
1.  IDE 从新打开的窗口中检索选定内容上下文，并将其放入全局选定内容上下文。 如果选定内容上下文使用 HIERARCHY_DONTPROPAGATE 或 SELCONTAINER_DONTPROPAGATE，该信息不会传播到全局上下文。 有关详细信息，请参阅[用户到反馈](../../extensibility/internals/feedback-to-the-user.md)。  
  
2.  通知事件会广播到任何请求它们的 VSPackage。  
  
3.  VSPackage 作用于它通过执行如更新层次结构中，重新激活一种工具或其他类似的任务的活动接收的事件。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [在 Visual Studio 中的层次结构](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [所选内容和在 IDE 中的货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [项目类型](../../extensibility/internals/project-types.md)
