---
title: "提供以大纲方式显示语言服务中的支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fd353e39e3e3edbdbdb929fa16abb74126dbbc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>如何： 扩展大纲显示在提供支持，旧语言服务
有两个选项用于扩展对你仅仅是支持的语言的大纲显示支持**折叠到定义**命令。 你可以添加控制编辑器的大纲区域，并添加客户端控制大纲区域。  
  
## <a name="adding-editor-controlled-outline-regions"></a>添加控制编辑器的大纲区域  
 使用此方法来创建大纲区域，然后允许编辑器来处理是否区域将展开，折叠状态，等等。 这两个提供大纲显示支持选项，此选项是最不可靠。 此选项，你创建新的大纲区域文本使用的指定范围内<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>。 创建此区域后，编辑器由控制其行为。 使用以下过程来实现控制编辑器的大纲区域。  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>若要实现控制编辑器的大纲区域  
  
1.  调用`QueryService`为<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     这将返回一个指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，并传入给定的文本缓冲区的指针。 这将返回一个指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>缓冲区的对象。  
  
3.  调用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>为指向的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>。  
  
4.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>以添加一个或多新一次大纲区域。  
  
     此方法允许你指定的大纲、 现有的大纲区域是删除还是保留，和大纲区域是展开还是折叠的默认值的文本范围。  
  
## <a name="adding-client-controlled-outline-regions"></a>添加客户端控制大纲区域  
 使用此方法实现客户端控制 （或智能） 以大纲方式显示如供[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]语言服务。 为了销毁旧的大纲区域时它们将变为无效并根据需要创建新的大纲区域，管理其自己以大纲方式显示的语言服务将监视的文本缓冲区内容。  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>若要实现客户端控制大纲区域  
  
1.  调用`QueryService`为<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。 这将返回一个指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，并传入给定的文本缓冲区的指针。 这将确定是否隐藏的文本会话已存在缓冲区。  
  
3.  如果文本会话已存在，则不需要创建一个，，指向现有<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>返回对象。 此指针可用于枚举和创建大纲区域。 否则，调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>创建隐藏的文本会话缓冲区。 指向的指针<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>返回对象。  
  
    > [!NOTE]
    >  当调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>，你可以指定隐藏的文本客户端 (即，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>对象)。 此客户端会通知你时隐藏文本或大纲区域是展开还是折叠的用户。  
  
4.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>结构) 参数： 指定的值<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>中`iType`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构以指示您要创建大纲区域，而不是隐藏的区域。 指定区域是客户端控制或在编辑器控制`dwBehavior`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构。 智能大纲显示实现可以包含多种编辑器和客户端控制大纲区域。 指定当大纲区域处于折叠状态，如"..."，在显示的横幅文本`pszBanner`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构。 隐藏区域的编辑器的默认横幅文本是"..."。