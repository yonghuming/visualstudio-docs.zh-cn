---
title: "如何：对状态栏的进度栏区域进行编程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "状态栏, 进度栏区域"
  - "进度栏, 状态栏"
  - "状态栏, 编程"
ms.assetid: 4b54616a-8c20-436d-b764-f2380e5760f2
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 如何：对状态栏的进度栏区域进行编程
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 状态栏的进度栏区域显示快速操作增量进度，例如，将文件保存到磁盘。  
  
### 使用 Visual Studio 状态栏的进度栏区域  
  
1.  获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 接口的实例，能通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 服务。  
  
2.  初始化进度栏到起始值通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> 方法。  
  
3.  更新进度栏，操作继续使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> 方法设置新值。  
  
## 示例  
 此示例演示如何初始化和更新进度栏。  
  
 [!CODE [VSSDKProgressStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkprogressstatusbar#1)]  
  
 在此示例中，代码:  
  
-   获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 接口的实例。 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> services。  
  
-   初始化进度栏对特定起始值通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> 方法。  
  
-   使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> 方法，通过循环 `for` 循环和更新进度栏值模拟操作。  
  
-   使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> 方法，清除进度栏。  
  
## 请参阅  
 [扩展状态栏](../extensibility/extending-the-status-bar.md)   
 [如何：读取和写入到“状态栏”的“反馈区域”](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [如何：使用状态栏的动画区域](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [如何：对状态栏的设计器区域进行编程](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)