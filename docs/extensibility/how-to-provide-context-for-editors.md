---
title: "如何： 为编辑器提供的上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6687ce3ed73a96778b84cec6e77d5c0b3145702d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-context-for-editors"></a>如何： 为编辑器提供的上下文
编辑器上下文处于活动状态，仅当编辑器具有焦点或立即之前焦点移动到工具窗口具有焦点时。 你可以通过执行以下编辑器提供上下文：  
  
1.  创建上下文包。  
  
2.  将上下文包发布到所选内容元素标识符 (SEID)。  
  
3.  维护在包上下文。  
  
 通过以下过程介绍这些任务。 有关提供上下文的详细信息，请参阅**可靠编程**本主题中更高版本。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>为编辑器或设计器创建上下文包  
  
1.  调用`QueryService`上你<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>接口<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>服务。  
  
     指向的指针<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>接口将返回。  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>方法来创建一个新的上下文或子上下文包。  
  
     指向的指针<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>接口将返回。  
  
3.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>方法将属性、 查找关键字或 F1 关键字添加到上下文或子上下文包。  
  
4.  如果要创建一个包，子上下文，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>方法以将子上下文包链接到父上下文包。  
  
5.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>可以接收通知时**动态帮助**窗口即将更新。  
  
     具有**动态帮助**窗口调用你的编辑器已准备好更新使你有机会延迟将上下文切换更新为止。 这样可以提高性能，因为它可让你延迟运行耗时的算法，直到系统空闲时间可用。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>若要将上下文包发布到 SEID  
  
1.  调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服务返回一个指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>接口。  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>，指定的元素标识符 (`elementid`参数) 的 SEID_UserContext 以指示要将上下文传递给全局级别的值。  
  
3.  当编辑器或设计器变为活动、 中的值其<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>对象会传播到全球的选择。 你只需完成一次每个会话，此过程，然后将存储指向你调用时创建的全局上下文的指针<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>。  
  
### <a name="to-maintain-the-context-bag"></a>若要维护的上下文包  
  
1.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>以确保**动态帮助**之前它将更新，窗口将调用编辑器或设计器。  
  
     已调用每个上下文包<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>上下文包创建，并且已实现后<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>，IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>通知上下文提供程序上下文包将会更新。 你可以使用此调用之前更改的特性和关键字在上下文包和任何子上下文包，**动态帮助**窗口更新发生。  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>对上下文包，以指示该编辑器或设计器具有新的上下文。  
  
     当**动态帮助**窗口调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>以指示它正在更新，编辑器或设计器可以在该时间更新父上下文包和任何子上下文包为适当的上下文。  
  
    > [!NOTE]
    >  `SetDirty`标志将自动设置为`true`每当添加或移除从上下文包上下文。 **动态帮助**窗口仅调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>对上下文包如果`SetDirty`标志设置为`true`。 重置为`false`更新后。  
  
3.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>将上下文添加到活动的上下文集合或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>删除上下文。  
  
## <a name="robust-programming"></a>可靠编程  
 如果你正在编写自己的编辑器，则必须完成所有三个本主题为编辑器中提供的上下文中的过程。  
  
> [!NOTE]
>  若要正确激活的编辑器或设计器窗口并确保命令路由已正确更新，必须调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>组件以使其焦点窗口上。  
  
 SEID 是更改基于所选内容的属性的集合。 提供通过全局选择了 SEID 信息。 全局选择连接到由触发的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>接口，并且已将所有内容的列表选择 （当前编辑器、 当前工具窗口、 当前层次结构等）。  
  
 为编辑器和设计器，可以每当更改的上下文中将光标移动在某个词低效不断更新上下文包。 若要使更新更加高效随时检测编辑器或设计器窗口中移动光标，你可以调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>。 执行此操作允许你保存上下文更改，直到空闲时间，并且 IDE 的上下文服务将通知发送到编辑器或设计器，可**动态帮助**窗口正在更新。 在"维护上下文包"过程中本主题中使用此方法。  
  
 提供你的编辑器或设计器中活动的上下文后, 应提供特定的 F1 关键字，以允许用户获取有关的编辑器或设计器本身的帮助。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>