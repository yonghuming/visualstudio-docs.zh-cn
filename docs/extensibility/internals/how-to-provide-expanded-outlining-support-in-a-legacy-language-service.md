---
title: "提供以大纲方式显示语言服务中的支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>如何︰ 提供旧语言服务中的扩展大纲显示支持
有关扩展您仅仅是支持的语言的大纲显示支持的两个选项**折叠到定义**命令。 您可以添加编辑器控制大纲区域，并添加客户端控制大纲区域。  
  
## <a name="adding-editor-controlled-outline-regions"></a>添加编辑器控制大纲区域  
 使用此方法创建大纲区域，然后允许编辑器来处理是否展开该区域，折叠状态，等等。 用于提供大纲显示支持的两个选项，此选项是最不可靠。 对于此选项，您创建一个新的大纲区域通过指定的文本范围的使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 创建此区域后，由编辑器中控制其行为。 使用以下过程来实现编辑器控制大纲区域。  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>若要实现编辑器控制大纲区域  
  
1.  调用`QueryService`为<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     这将返回一个指针，到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，并传入一个给定的文本缓冲区的指针。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> 这将返回一个指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>对象缓冲区。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>对<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>的指针</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession></xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>调用  
  
4.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>以添加一个或更多新一次大纲区域。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     此方法允许您指定的文本轮廓，现有的大纲区域是删除还是保留，和大纲区域是展开还是折叠默认情况下是否范围。  
  
## <a name="adding-client-controlled-outline-regions"></a>添加客户端控制大纲区域  
 使用这种方法向客户端控制 （或明智） 的实现以大纲方式显示喜欢使用[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]语言服务。 用于管理其自己以大纲方式显示的语言服务监视将文本缓冲区的内容，以便在将变为无效时销毁旧大纲区域并根据需要创建新的大纲区域。  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>若要实现客户端控制大纲区域  
  
1.  调用`QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 这将返回一个指针，到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，并传入一个给定的文本缓冲区的指针。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> 这可确定是否隐藏的文本已存在会话的缓冲区。  
  
3.  如果文本会话已存在，则不需要创建一个，和一个指向现有<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>返回对象。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 使用此指针来枚举以及创建大纲区域。 否则，调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>创建隐藏的文本，会话的缓冲区。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 一个指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>返回对象。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  当您调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>，您可以指定一个隐藏的文本，客户端 (即，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>对象)。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 此客户端会通知您时隐藏的文本或大纲区域是展开还是折叠的用户。  
  
4.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>结构) 参数︰ 将值指定为<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>中`iType`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构指示要创建大纲区域，而不是隐藏的区域。</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 指定区域是客户端控制或在编辑器中控制`dwBehavior`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构。</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 智能的大纲显示实现可以包含多种编辑器和客户端控制大纲区域。 指定当大纲区域处于折叠状态，如"..."，在显示的横幅文本`pszBanner`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构。</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 隐藏区域的编辑器的默认标题文本是"..."。
