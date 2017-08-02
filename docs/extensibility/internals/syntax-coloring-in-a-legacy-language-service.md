---
title: "语法着色在传统语言服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语法着色"
  - "语言服务功能︰ 语法着色"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 语法着色在传统语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用着色服务标识语言的元素并显示它们与编辑器中指定的颜色。  
  
## Colorizer 模型  
 语言服务实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 接口，编辑然后使用。  如下图所示，此实现是从语言服务的一个单独的对象，。  
  
 ![SVC 着色程序图](~/docs/extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
简单的 colorizer 模型  
  
> [!NOTE]
>  语法着色服务与 colorizing 文本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 常规结构。  有关支持 colorizing 的 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 常规 framework 的更多信息，请参见 [使用字体和颜色](../../extensibility/using-fonts-and-colors.md)。  
  
 除了 colorizer 外，语言服务可以提供要用于通过播发访问它提供自定义可着色项的自定义可着色项。  通过实现在同一对象的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 接口执行此 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 实现接口。  它返回自定义可着色项的数目，当编辑器 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 调用方法时，因此，它返回单个自定义可着色项，当编辑器 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 调用方法时。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 方法返回对象 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 实现接口。  如果语言服务支持 24 位或深颜色值，则它必须实现在对象的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 接口和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 接口相同。  
  
## VSPackage 如何使用语言服务 Colorizer  
  
1.  VSPackage 必须获取相应的语言服务，需要语言服务 VSPackage 执行以下操作:  
  
    1.  使用实现接口 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 捕获的对象 colorized 的文本。  
  
         文本通常会显示使用对象实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 接口。  
  
    2.  获取语言服务通过查询 VSPackage 的服务提供程序语言服务的 GUID。  语言服务在注册表中确定的文件扩展名。  
  
    3.  关联语言服务与 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 通过调用其 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 方法。  
  
2.  VSPackage 现在可以获取和使用 colorizer 对象如下所示:  
  
    > [!NOTE]
    >  使用核心编辑器的 Vspackage 不需要显式获取语言服务的 colorizer 对象。  当核心编辑器的实例获取相应的语言服务，它执行公开的所有着色任务示。  
  
    1.  通过调用语言服务的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 对象的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 方法获取语言服务的 colorizer 对象，实现 `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> 接口，。  
  
    2.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法获取文本特定范围的 colorizer 信息。  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 返回值，则在 colorized 的文本范围的每个字符的。  值是索引为或默认值可着色项列表维护由核心编辑器或自定义可着色项列表维护的语言服务的可着色项列表。  
  
    3.  使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法返回的着色信息显示选定的文本。  
  
> [!NOTE]
>  除了使用语言服务 colorizer 外， VSPackage 还可以使用泛型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 文本着色机制。  有关此结构的更多信息，请参见 [使用字体和颜色](../../extensibility/using-fonts-and-colors.md)。  
  
## 本节内容  
 [实现功能: 语法着色](../../extensibility/internals/implementing-syntax-coloring.md)  
 讨论如何编辑访问语言服务的语法着色，以及语言服务必须实现支持语法着色。  
  
 [如何: 使用内置可着色的项](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 演示如何使用从语言服务的内置可着色项。  
  
 [自定义可着色的项](../../extensibility/internals/custom-colorable-items.md)  
 讨论如何实现自定义可着色项。  
  
## 请参阅  
 [使用字体和颜色](../../extensibility/using-fonts-and-colors.md)