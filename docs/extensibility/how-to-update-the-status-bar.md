---
title: "如何: 更新状态栏 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的更新状态栏"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何: 更新状态栏
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**状态栏** 是控制条位于包含一个或多个状态文本行或指示符许多应用程序窗口的底部。  
  
### 更新状态栏  
  
1.  在每个单独视图对象 \(DocView\) 的实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 编辑器提供，如窗体视图和代码视图。  
  
2.  当 IDE 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>时，通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>方法更新。 **状态栏** 的信息。  
  
    > [!NOTE]
    >  ，只有在最初激活时， IDE 会调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 文档窗口。  对于时间剩下的时间文档窗口处于活动状态，则必须更新 **状态栏** 信息，当编辑器的状态更改。  
  
## 可靠编程  
 **状态栏** 包含四个不同字段:  
  
-   状态文本  
  
-   Progress bar  
  
-   事件的图标  
  
-   编辑信息  
  
 有关更多信息，请参见 [状态栏](/visual-cpp/mfc/status-bars)。  
  
 激活时，时， IDE 自动调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 实现的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 方法文档窗口。  
  
 VSPackage 来实现用于更新在状态栏的状态文本内容。  IDE 重置此字符串为 “就绪”，如果状态文本字段设置为文本 \(""\) 在空闲时间。  
  
## 请参阅  
 [状态栏](/visual-cpp/mfc/status-bars)