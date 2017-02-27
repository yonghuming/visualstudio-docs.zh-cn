---
title: "旧语言服务模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言服务、 模型"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 旧语言服务模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

语言服务定义元素和功能的特定语言的和用于提供编辑的信息特定于该语言。  例如，编辑器需要知道该语言的元素和关键字为了支持语法着色。  
  
 语言服务紧密地使用编辑器和包含编辑器的视图管理的文本缓冲区一起使用。  Microsoft IntelliSense **快速信息** 选项是语言服务提供的功能的示例。  
  
## 最小的语言服务  
 最基本的语言服务包含以下两个对象:  
  
-   *语言服务* 实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 接口。  语言服务具有有关语言的信息，包括其名称、文件扩展名、代码窗口管理器和 colorizer。  
  
-   *colorizer* 实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 接口。  
  
 以下概念绘制演示一个基本的语言服务的模型。  
  
 ![语言服务模型图](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
基本语言服务模型  
  
 文档窗口承载 *文档* 的 *视图* 编辑器，在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 核心编辑器。  文档视图和文本缓冲区由编辑器拥有。  这些对象与 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用通过专用调用*代码窗口的*文档窗口。  在代码窗口是由 IDE 创建控件的<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 对象包含。  
  
 当具有特定扩展名的文件加载时，编辑器找到语言服务与该扩展并向其传递代码窗口通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 方法。  语言服务返回 *代码窗口管理器*， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 实现接口。  
  
 下表提供该模型中的对象的概述。  
  
|组件|对象|功能|  
|--------|--------|--------|  
|文本缓冲区|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode 读\/写文本流。  使用其他编码文本是可能的。|  
|代码窗口|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|包含一个或多个文本视图的文档窗口。  当 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 则多文档界面 \(mdi\) \(MDI\) 模式，代码窗口是 MDI 子窗体。|  
|text " 视图|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|使用该键盘和鼠标，它们使用户能够导航和视图文本的窗口。  文本视图显示给用户用作编辑。  在普通编辑器窗口、 " 输出 " 窗口和 " 即时 " 窗口可以使用文本视图。  此外，您可以在代码窗口中的一个或多个文本视图。|  
|text 管理器|管理的 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 服务，则获取一 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 指针|维护所有元素共享的通用信息前面所述的元素。|  
|语言服务|实现依赖项;实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|提供编辑器以特定语言的信息 \(如显示的语法的对象，语句完成和括号匹配。|  
  
## 请参阅  
 [文档数据和自定义编辑器中的文档视图](../../extensibility/document-data-and-document-view-in-custom-editors.md)