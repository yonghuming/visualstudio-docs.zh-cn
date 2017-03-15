---
title: "通过使用旧 API 访问文本视图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的文本视图"
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 通过使用旧 API 访问文本视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本视图是在文本缓冲区存储文本呈现。  如以下章节所示，可以访问文本视图使用传统的 API。  
  
## 文本视图对象  
 每个视图与自己的文本缓冲区，因此，视图中的数据的 windows 缓冲区。  下图显示文本视图对象的关键接口，该接口由 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>表示。  
  
 ![Visual Studio 文本视图对象](../extensibility/media/vstextview.png "vstextview")  
文本视图对象  
  
 视图存在缓冲区的文本模式。  它包括诸如自动换行和大纲显示，因此，与您在视图中看到非 text 的精确表示缓冲区中的。  
  
 ，该视图在之前，操作视图。利用这些其他服务或进程截获传入的命令和操作。  若要执行此操作的最常见的服务是语言服务。  语言服务可能需要，例如，截获 enter 键的命令可以提供缩进行为或工具提示的自定义。  
  
## 将功能添加到文本视图  
 可以通过处理特定按键自定义文本视图行为。  若要截获，但您实现在对象的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> ，并提供命令目标 \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) 监控和截获命令。  
  
 文本视图的命令筛选器使用的体系结构。  新的命令筛选器 \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 对象\) 添加到该序列通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法。  
  
 使用 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` 接口，文本视图的事件通知提供。  实现在客户端对象的此接口接收更改的通知到文本视图的。  显示该接口在文本视图通过在文本视图的 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 接口接收更改的通知从视图的。  
  
## 请参阅  
 [通过使用旧 API 更改视图设置](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [使用文本管理器来监视全局设置](../extensibility/using-the-text-manager-to-monitor-global-settings.md)