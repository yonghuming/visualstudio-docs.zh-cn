---
title: "旧 API 中的文本缓冲区事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 39ac6a711278950d09ed16b157fc89980144e3d0
ms.lasthandoff: 02/22/2017

---
# <a name="text-buffer-events-in-the-legacy-api"></a>旧 API 中的文本缓冲区事件
文本缓冲区对象发出多个不同的事件，您可以对不同的情况作出响应。  
  
 当使用传统的 API 时，应实现以下接口，以便接收文本缓冲区发生更改的通知。 将文本缓冲区使用接口公开`IConnectionPointContainer`文本缓冲区以接收通知的行上的接口将更改从缓冲区。 有关详细信息，请参阅[如何︰ 为与旧 API 的文本缓冲区事件注册](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)。 情况下`IVsTextStreamEvents`或`IVsTextLinesEvents`接口，则返回的更改中的任一一个-或两维坐标表示，分别。  
  
## <a name="text-buffer-interfaces"></a>文本缓冲区接口  
 以下是实现文本缓冲区对象的接口。  
  
|接口|说明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可以创建复合操作 （即单个撤消/重做单位进行分组的操作）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|使文本缓冲区由管理的文档数据的持久性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本服务;由多个客户端使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供了读取和写入使用二维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 面向流的、 按顺序访问缓冲区中的文本。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供了读取和写入使用一维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供对属性的泛型集合的访问。 最重要属性是缓冲区的名称或的名字对象。 通过创建 GUID 并使用它作为键，可以在具有此接口的缓冲区中存储您自己的随机数据。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer></xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支持连接点事件。|  
  
## <a name="text-buffer-event-interfaces"></a>文本缓冲区事件接口  
 以下是用于文本缓冲区事件通知的接口。  
  
|接口|说明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|在新的语言服务是与文本缓冲区相关联时，通知客户端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|初始化文本缓冲区时和在文本缓冲区中的数据发生更改时通知客户端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|通知客户端的更改在一维坐标中的基础文本缓冲区。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|通知客户端的更改在二维坐标中的基础文本缓冲区。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|通知客户端的用户数据的更改。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|通知客户端的最后一个提交笔势以触发该事件，并提供的更改的文本范围。 `IVsPreliminaryTextChangeCommitEvents`接口，则不激发以响应撤消或重做命令。 对于具有撤消管理器的缓冲区只激发事件。 `IVsPreliminaryTextChangeCommitEvents`引发在其他事件，如整齐排列之前以确保在提交更改之前，其他事件执行更改文本。 你的 VSPackage 必须监视任何一个`IVsPreliminaryTextChangeCommitEvents`接口或`IVsFinalTextChangeCommitEvents`界面，但不要同时使用两者。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|通知客户端的最后一个提交笔势以触发该事件，并提供的更改的文本范围。 `IVsFinalTextChangeCommitEvents`接口，则不激发以响应撤消或重做命令。 对于具有撤消管理器的缓冲区只激发事件。 `IVsFinalTextChangeCommitEvents`为使用只适合由语言服务或对编辑具有完全控制的其他对象。 你的 VSPackage 必须监视任何一个`IVsPreliminaryTextChangeCommitEvents`接口或`IVsFinalTextChangeCommitEvents`界面，但不要同时使用两者。|  
  
## <a name="see-also"></a>另请参阅  
 [通过使用旧 API 访问文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [如何︰ 为与旧 API 的文本缓冲区事件注册](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
