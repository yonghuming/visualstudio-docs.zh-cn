---
title: "通过使用旧 API 访问文本缓冲区 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的文本缓冲区"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 通过使用旧 API 访问文本缓冲区
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

中的文本与管理文本流和文件持久性负责。  虽然缓冲区可以读取或写入其他格式，使用 Unicode，与缓冲区的所有普通的通信执行。  在传统 API，文本缓冲区可以使用一个或二维坐标系标识缓冲区的字符位置。  
  
## 一个和两维的坐标系  
 一维坐标位置根据第一个字符的字符位置缓冲区，如 147。  使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 界面访问一个一维位置缓冲区。  二维坐标系基于行，并对索引。  例如，在缓冲区中的字符在 43， 5 在行 43，在第一个字符右侧的五个字符在该行。  您访问缓冲区的二维位置使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 接口。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 接口由文本缓冲区对象 \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\) 实现使用 `QueryInterface`，并且可以彼此进行访问。  下图显示这些并在 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>的其他关键接口。  
  
 ![文本缓冲区对象](~/extensibility/media/vstextbuffer.gif "vsTextBuffer")  
文本缓冲区对象  
  
 虽然任何坐标系统在文本缓冲区工作，则会优化使用二维坐标。  一维坐标系统可以创建性能开销。  因此，请使用二维坐标系尽可能。  
  
 文本缓冲区的第二责任是文件的持久性。  为此，文本缓冲区对象实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 和为持久性和其他环境元素的文档数据对象元素涉及的项目项。  有关更多信息，请参见 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)。  
  
## 本节内容  
 [通过使用旧 API 更改视图设置](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 使用传统的 API，说明如何更改视图设置。  
  
 [使用文本管理器来监视全局设置](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 解释如何使用文本管理器监视全局设置。  
  
## 请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)