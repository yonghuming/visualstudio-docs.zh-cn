---
title: "如何︰ 为编辑器提供的上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 17
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
ms.openlocfilehash: 362cd554e0723b1137d033440c9844d6cf3e59dd
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-context-for-editors"></a>如何︰ 为编辑器提供的上下文
编辑器上下文处于活动状态，仅在编辑器具有焦点或之前将焦点移动到工具窗口具有焦点时。 您可以通过执行以下用于编辑器提供上下文︰  
  
1.  创建上下文包。  
  
2.  将上下文包发布到所选内容元素标识符 (SEID)。  
  
3.  维护包中的上下文。  
  
 下面的过程都介绍这些任务。 有关提供上下文的详细信息，请参阅**可靠编程**本主题中更高版本。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>若要为编辑者或设计器创建上下文包  
  
1.  调用`QueryService`上您<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>接口<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>服务。</xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     一个指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>接口将返回。</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>方法来创建一个新的上下文或子上下文包。</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>  
  
     一个指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>接口将返回。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
3.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>方法以向上下文或子上下文包中添加属性、 查找关键字或 F1 关键字。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
4.  如果要创建包的子上下文，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>方法以将子上下文包链接到父上下文包。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>  
  
5.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>以接收通知时**动态帮助**窗口即将更新。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>  
  
     具有**动态帮助**窗口调用您的编辑器已准备好更新为您提供机会来延迟状态，直到此更新发生更改的上下文。 这样可以提高性能，因为它允许您以后再运行耗时的算法，直到系统空闲时才可用。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>若要将上下文包发布到 SEID  
  
1.  调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服务返回一个指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> </xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>，指定元素标识符 (`elementid`参数) 值以指示要将上下文传递给全局级别的 SEID_UserContext。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
3.  当编辑器或设计器变为活动状态、 中的值及其<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>对象传播到全局选择。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 你只需以完成此过程一次每个会话，然后将存储指向调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>时创建的全局上下文的指针  
  
### <a name="to-maintain-the-context-bag"></a>若要维护的上下文包  
  
1.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>以确保**动态帮助**窗口调用编辑器或设计器之前它将更新。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
     已调用每个上下文包<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>上下文包创建，并且已实现后<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>，IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>以通知上下文提供程序将更新上下文包。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> 可以使用此调用之前更改特性和关键字在上下文包，和任何子上下文包、**动态帮助**窗口更新进行一次。  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>对上下文包，以指示的编辑器或设计器具有新的上下文。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>  
  
     当**动态帮助**窗口调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>以指示它正在更新，编辑器或设计器可以在该时间更新为父上下文包和任何子上下文包适当的上下文。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>  
  
    > [!NOTE]
    >  `SetDirty`标志将自动设置为`true`每当添加或删除从上下文包上下文。 **动态帮助**窗口仅调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>对上下文包如果`SetDirty`标志设置为`true`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 重置为`false`更新后的。  
  
3.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>将上下文添加到活动的上下文集合或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>删除上下文。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
## <a name="robust-programming"></a>可靠编程  
 如果您正在编写您自己的编辑器，您必须完成所有三个本主题为编辑器中提供的上下文中的过程。  
  
> [!NOTE]
>  若要正确激活编辑器或设计器窗口并确保命令传送已正确更新，则必须调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>组件即可使其焦点窗口上。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
 SEID 是更改基于所选的属性的集合。 提供通过全局选择了 SEID 信息。 全局选择连接到由触发的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>接口，并且已将所有内容的列表选择了 （当前编辑器、 当前工具窗口、 当前层次结构等）。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>  
  
 编辑器和设计人员，在何种上下文可以每当更改光标移动在某个词是效率低下，来不断更新的上下文包。 若要使更新更高效随时检测光标移动在编辑器或设计器窗口中，您可以调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> 这样做允许您能够将保存在上下文更改，直到空闲时间，并且 IDE 的上下文服务将发送通知到编辑器或设计器的**动态帮助**窗口更新。 在"维护上下文包"过程中本主题中使用此方法。  
  
 提供编辑器或设计器中活动的上下文后, 应提供特定的 F1 关键字，以允许用户获取的编辑器或设计器本身的帮助。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
