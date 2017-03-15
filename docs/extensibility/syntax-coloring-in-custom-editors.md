---
title: "语法着色中自定义编辑器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的语法着色"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 语法着色中自定义编辑器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio SDK 环境编辑，包括核心编辑器中，使用语言服务标识特定语法项，并显示具有给定的指定的颜色文档视图。  
  
## 着色要求  
 实现语言服务的 colorizer 的所有编辑器必须:  
  
1.  使用实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 的对象管理该文本 colorized 的和实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 的对象提供文本的文档视图。  
  
2.  获取一个接口特定语言服务通过查询使用的语言服务标识的 GUID 的 VSPackage 的服务提供程序。  
  
3.  调用实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>对象的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 方法。  此方法关联语言服务和 VSPackage 使用管理文本将 colorized 的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 实现。  
  
## 核心语言服务的 Colorizer 的编辑用法  
 在使用 colorizer 的语言服务由核心编辑器的实例时，获取分析和呈现的语言服务的 colorizer 的文本会自动发生不需要在部分的任何进一步的干预。  
  
 透明 IDE:  
  
-   调用 colorizer，因为需要分析和分析文本，当在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>的实现中添加或更改。  
  
-   确保文档视图中提供的显示由提供 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 实现是更新和重新绘制使用 colorizer 返回的信息。  
  
## 语言服务的 Colorizer 的非内核的编辑用法  
 非内核的编辑实例也可以使用语言服务的语法着色服务，但是，它们必须显式检索，并且应用服务的 colorizer 和重新绘制这些文档视图。  
  
 为此要求非内核的版本:  
  
1.  获取实现 `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>\) 的语言服务的 colorizer 对象 \(。  VSPackage 通过调用语言服务的接口的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 方法执行此操作。  
  
2.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法请求文本特定范围 colorized。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法返回值，则在 colorized 的文本范围的每个字母的。  它还标识文本范围作为可着色项的特定类型，如注释、关键字或数据类型。  
  
3.  使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 返回的着色信息重新绘制并显示其文本。  
  
> [!NOTE]
>  除了使用语言服务的 colorizer 外， VSPackage 可以选择使用常规 Visual Studio SDK 环境文本着色机制。  有关此结构的更多信息，请参见 [使用字体和颜色](../extensibility/using-fonts-and-colors.md)。  
  
## 请参阅  
 [语法着色在传统语言服务](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [实现功能: 语法着色](../extensibility/internals/implementing-syntax-coloring.md)   
 [如何: 使用内置可着色的项](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自定义可着色的项](../extensibility/internals/custom-colorable-items.md)