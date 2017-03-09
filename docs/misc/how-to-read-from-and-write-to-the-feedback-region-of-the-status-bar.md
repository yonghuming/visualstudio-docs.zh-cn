---
title: "如何：读取和写入到“状态栏”的“反馈区域” | Microsoft Docs"
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
  - "反馈区域, 状态栏"
  - "状态栏, 反馈区域"
  - "状态栏, 概述"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 如何：读取和写入到“状态栏”的“反馈区域”
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 状态栏的反馈区域显示文本。  可以设置和检索文本，显示静态文本，并显示显示的文本。  
  
### 使用 Visual Studio 状态栏的反馈区域  
  
1.  获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 接口的实例，能通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 服务。  
  
2.  确定状态栏是否通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 实例的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> 方法冻结。  
  
3.  通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A> 方法并传入设置反馈区域的文本在文本字符串。  
  
4.  通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> 方法读取反馈区域的文本。  
  
## 示例  
 此示例演示如何写入文本演示如何使用和读取从反馈区域的文本。  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 在上面的示例中，代码进行以下操作:  
  
-   获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 接口的实例。 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> services。  
  
-   检查状态栏是否通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> 方法冻结。  
  
-   禁止进一步更新状态栏通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> 方法。  
  
-   通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> 方法读取状态栏的文本并在消息框中显示该  
  
-   允许更新状态栏通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> 和传递 0 在参数。  
  
-   清除内容状态栏通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> 方法。  
  
## 请参阅  
 [扩展状态栏](../extensibility/extending-the-status-bar.md)   
 [如何：对状态栏的进度栏区域进行编程](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [如何：使用状态栏的动画区域](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [如何：对状态栏的设计器区域进行编程](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)