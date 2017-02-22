---
title: "通过使用旧 API 的访问将文本层 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的文本图层"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 通过使用旧 API 的访问将文本层
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本层通常封装文本格式的某些方面。  例如， “功能时间”层隐藏文本在包含插入符号的功能之前或之后 \(文本插入点\)。  
  
 文本层位于缓冲区和视图之间，，并修改视图查看缓冲区的内容的方式。  
  
## text 层信息  
 下面的列表描述文本层如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]工作:  
  
-   在文本层的文本可使用语法着色和标记修饰。  
  
-   您当前不能实现拥有层。  
  
-   层显示 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，从 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>派生。  文本缓冲区也实现为层，可以查看过程 polymorphically 基础层。  
  
-   任意数量的层可以放在视图和缓冲区。  每个层仅处理层在其下，因此，视图主进程中最顶层的层。  \(该视图具有有关缓冲的某些信息。\)  
  
-   层会影响其下方仅层。  它不会影响上来的层在给定标准事件外。  
  
-   在编辑器中，隐藏文本、聚合文本和换行实现为层。  可以实现隐藏的和复合文本，但不适合直接与层。  有关更多信息，请参见[传统语言服务中的大纲显示](../extensibility/internals/outlining-in-a-legacy-language-service.md)和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>。  
  
-   每个文本层可通过 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> 接口公开自己的本地坐标系统。  ，当基础文本缓冲区可能只包含一行时，换行层，例如，可能包含两行。  
  
-   视图传递至层。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> 接口。  使用此接口协调项缓冲区坐标的视图坐标。  
  
-   任何层例如给定文本的复合文本层必须提供 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>的一个本地实现。  
  
-   除了 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>外，文本层必须实现 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 和激发在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> 接口的事件。  
  
## 请参阅  
 [语法着色中自定义编辑器](../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用旧 API 使用文本标记](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [通过使用旧 API 自定义编辑器控件和菜单](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)