---
title: "如何：使用状态栏的动画区域 | Microsoft Docs"
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
  - "状态栏, 编程"
  - "状态栏, 动画区域"
  - "动画区域, 状态栏"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 如何：使用状态栏的动画区域
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 状态栏的动画区域显示例如指示较长操作或不确定的长度的操作的循环的动画 \(，成多个项目在解决方案\)。  
  
### 使用 Visual Studio 状态栏的动画区域  
  
1.  获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 接口的实例，能通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 服务。  
  
2.  通过调用状态栏的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> 方法启动动画。  通过在 1 作为第一个参数的值和对事件的图标与第二个参数的值。  
  
3.  通过调用状态栏的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> 方法停止动画。  在 0 的作为第一个参数传递的值和对活动的图标的引用作为第二个参数的值。  
  
## 示例  
 此示例在动画区域演示如何运行内置动画。  
  
 [!CODE [VSSDKAnimationStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkanimationstatusbar#1)]  
  
## 请参阅  
 [扩展状态栏](../extensibility/extending-the-status-bar.md)   
 [如何：读取和写入到“状态栏”的“反馈区域”](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [如何：对状态栏的进度栏区域进行编程](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [如何：对状态栏的设计器区域进行编程](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)