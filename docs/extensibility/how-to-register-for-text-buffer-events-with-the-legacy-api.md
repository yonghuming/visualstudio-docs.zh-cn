---
title: "如何︰ 为与旧 API 的文本缓冲区事件注册 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
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
ms.openlocfilehash: b7da1dc26631294b6e41aa6335f2dca064c2831d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>如何︰ 为与旧 API 的文本缓冲区事件注册
如果正在使用传统的 API 来访问文本缓冲区，你应注册文本缓冲区事件，如下面的过程中所示。  
  
### <a name="to-advise-text-buffer-events"></a>向建议文本缓冲区事件  
  
1.  从指向在接口中的一个<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>，调用`QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>的指针</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
2.  调用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>方法，并传入要注册的事件的接口 ID。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>  
  
     例如，如果您想要注册，以便为<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>，然后将传递在接口 ID 的 IID_IVsTextLinesEvents。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>  
  
     文本缓冲区返回一个指向<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>适当的连接点对象的接口。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>  
  
3.  使用此指针，调用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>方法，并在一个指针传递到您想要为其注册，例如，事件接口的实现`IVsTextLinesEvents`接口。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>  
  
     该环境将返回的 cookie，您可以使用它来停止侦听事件，通过调用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>方法。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>  
  
## <a name="see-also"></a>另请参阅  
 [旧 API 中的文本缓冲区事件](../extensibility/text-buffer-events-in-the-legacy-api.md)
