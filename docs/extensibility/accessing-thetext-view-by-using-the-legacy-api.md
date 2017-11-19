---
title: "通过使用旧版 API 访问文本视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07ce61a0188802455c4e64b698344c3f275215bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>通过使用旧版 API 访问文本视图
文本视图是文本的一个演示文稿的文本缓冲区中存储。 可以通过以下部分中所示，使用旧的 API 来访问文本视图。  
  
## <a name="text-view-object"></a>文本视图对象  
 每个视图是关联使用其自己的文本缓冲区，并且视图在缓冲区中数据的窗口。 下图显示的文本视图对象，表示密钥的接口<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>。  
  
 ![Visual Studio 文本视图对象](../extensibility/media/vstextview.gif "vstextview")  
文本视图对象  
  
 视图是一种提供缓冲区中的文本。 它包括功能，如自动换行，并以大纲方式显示，以便在视图中看到的内容不是精确地表示的缓冲区中的文本。  
  
 视图使其他服务或进程可截获传入命令，并对它们之前对它们，视图的作用。 要执行此操作的最常见服务是一个语言服务。 语言服务可能需要，例如，截获 ENTER 键，以提供自定义缩进的行为或工具提示的命令。  
  
## <a name="adding-functionality-to-the-text-view"></a>将功能添加到文本视图  
 您可以通过处理特定击键自定义文本视图行为。 若要截获击键，则实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>你的对象，并提供了一个命令目标 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 到监视器和截距命令。  
  
 文本视图使用命令筛选器的顺序的体系结构。 新的命令筛选器 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>对象) 通过调用添加到 sequence<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。  
  
 文本视图的事件通知通过使用提供`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents`接口。 在你的客户端对象来接收到文本视图的更改的通知上实现此接口。 通过使用公开此接口到文本视图<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>文本视图从视图中接收通知的更改上的接口。  
  
## <a name="see-also"></a>另请参阅  
 [通过使用旧版 API 更改视图设置](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [使用文本管理器来监视全局设置](../extensibility/using-the-text-manager-to-monitor-global-settings.md)