---
title: "旧版 API 中的文本缓冲区事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5118fe29463368bcca90e21830e1418d41c18339
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="text-buffer-events-in-the-legacy-api"></a>旧版 API 中的文本缓冲区事件
文本缓冲区对象发出多个不同的事件，您可以对不同的情况作出响应。  
  
 当你使用旧的 API 时，应实现以下接口，以便接收到文本缓冲区的更改的通知。 公开的接口连接到文本缓冲区使用`IConnectionPointContainer`接口上要接收通知的行的文本缓冲区将更改从缓冲区。 有关详细信息，请参阅[如何： 为与旧版 API 的文本缓冲区事件注册](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)。 情况下`IVsTextStreamEvents`或`IVsTextLinesEvents`接口，则返回的更改中的任一一个-或两维坐标表示，分别。  
  
## <a name="text-buffer-interfaces"></a>文本缓冲区接口  
 以下是由文本缓冲区对象实现的接口。  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|允许创建复合操作 （即，在单个撤消/重做单元进行分组的操作）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|启用管理的文本缓冲区的文档数据的持续的性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本服务; 示例：由多个客户端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供读取和写入使用二维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 面向流的、 按顺序访问缓冲区中的文本。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供读取和写入使用一维坐标的功能。 继承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供对属性的泛型集合的访问。 最重要的属性是名称或标记时的缓冲区。 通过创建 GUID 并将其作为一个键，可以将自己的随机数据存储在具有此接口的缓冲区。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|事件支持连接点。|  
  
## <a name="text-buffer-event-interfaces"></a>文本缓冲区事件接口  
 以下是文本缓冲区事件通知的接口。  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|当与文本缓冲区关联的新语言服务时，通知客户端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|文本缓冲区初始化时和文本缓冲区中的数据发生更改时，通知客户端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|通知客户端的对一维坐标中的基础文本缓冲区的更改。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|通知客户端的更改到二维坐标中的基础文本缓冲区。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|通知客户端的对用户数据的更改。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|通知客户端的最后一个提交手势以触发该事件，并提供的文本更改范围。 `IVsPreliminaryTextChangeCommitEvents`接口不激发以响应撤消或重做命令。 针对具有撤消管理器的缓冲区的仅触发事件。 `IVsPreliminaryTextChangeCommitEvents`不会触发之前其他事件，如整齐排列，为了确保在提交更改之前，其他事件请勿更改文本。 你的 VSPackage 必须监视`IVsPreliminaryTextChangeCommitEvents`接口或`IVsFinalTextChangeCommitEvents`接口，但不是两者。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|通知客户端的最后一个提交手势以触发该事件，并提供的文本更改范围。 `IVsFinalTextChangeCommitEvents`接口不激发以响应撤消或重做命令。 针对具有撤消管理器的缓冲区的仅触发事件。 `IVsFinalTextChangeCommitEvents`适合使用仅由语言服务或对编辑具有完全控制其他对象。 你的 VSPackage 必须监视`IVsPreliminaryTextChangeCommitEvents`接口或`IVsFinalTextChangeCommitEvents`接口，但不是两者。|  
  
## <a name="see-also"></a>另请参阅  
 [通过使用旧版 API 访问文本缓冲区](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [如何： 为与旧版 API 的文本缓冲区事件注册](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)