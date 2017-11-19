---
title: "选择上下文对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe4921e48c978b1073c985d4c11f11a14f3b351c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="selection-context-objects"></a>选择上下文对象
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 使用全局选择上下文对象来确定在 IDE 中应显示的内容。 在 IDE 中的每个窗口可以推送到全局选择上下文自己选择上下文对象。 该窗口拥有焦点时，IDE 窗口中的值更新全局选择上下文。 有关详细信息，请参阅[向用户反馈](../../extensibility/internals/feedback-to-the-user.md)。  
  
 每个窗口框架或在 IDE 中的站点具有一个称为服务<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。 由你放置在该窗口框架的 VSPackage 创建的对象必须调用`QueryService`方法以获取指向<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>接口。  
  
 框架窗口可以保留部分可能会传播到全局选择上下文将在启动时从其选择上下文信息。 此功能可用于工具窗口可能具有以开头的空的选择。  
  
 修改 Vspackage 可以监视的全局选择上下文触发器事件。 Vspackage 可以通过实现来执行以下任务`IVsTrackSelectionEx`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>接口：  
  
-   更新层次结构中当前处于活动状态的文件。  
  
-   监视器更改为某些类型的元素。 例如，如果你的 VSPackage 使用特殊**属性**窗口中，你可以监视活动中的更改**属性**窗口，然后重新启动你的帐户在需要时。  
  
 按以下顺序显示选定内容跟踪的典型的过程。  
  
1.  IDE 从新打开的窗口检索所选内容上下文，并将其放在全局选择上下文中。 如果选择上下文使用 HIERARCHY_DONTPROPAGATE 或 SELCONTAINER_DONTPROPAGATE，该信息都不会传播到全局上下文中。 有关详细信息，请参阅[向用户反馈](../../extensibility/internals/feedback-to-the-user.md)。  
  
2.  通知事件会传播至任何请求它们的 VSPackage。  
  
3.  VSPackage 作用于它接收通过执行活动，例如更新层次结构中，重新激活一个工具或其他类似的任务的事件。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Visual Studio 中的层次结构](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [选择和 IDE 中的货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [项目类型](../../extensibility/internals/project-types.md)