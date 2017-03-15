---
title: "如何: 实现查找和替换机制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的查找和替换"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何: 实现查找和替换机制
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 提供实现查找两种方式\/替换。  一种方法是通过文本图像对 shell 并让其搜索，显示和替换文本的句柄。  这允许用户指定多个文本范围。  或者， VSPackage 中控制此功能。  在这两种情况下必须通知当前目标的 shell，所有的目标打开文档。  
  
### 若要实现 " 查找\/替换  
  
1.  实现在框架属性返回的一 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> 接口的对象 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 或 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。  如果创建自定义编辑器，为自定义编辑器类的一部分，则应实现此接口。  
  
2.  使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> 方法指定编辑器支持和指定的选项时是否实现文本映像搜索。  
  
     如果编辑器支持搜索文本的图像，请实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>。  
  
     否则，请实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>。  
  
3.  如果执行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> 方法，可以通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> 接口简化搜索的任务。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>