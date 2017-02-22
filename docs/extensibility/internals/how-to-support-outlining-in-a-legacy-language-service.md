---
title: "如何︰ 支持传统语言服务中的大纲显示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，折叠到定义命令"
  - "语言服务，支持折叠到定义命令"
  - "隐藏的文本折叠到定义命令"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何︰ 支持传统语言服务中的大纲显示
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以大纲方式显示用于展开或折叠的文本的不同区域。 使用方式大纲显示可通过不同的语言以不同方式定义。 有关更多信息，请参见[大纲显示](../../ide/outlining.md)。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现以大纲方式显示的新方法的详细信息，请参阅 [演练: 大纲显示](../../extensibility/walkthrough-outlining.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
 以下代码演示了如何为您的语言服务支持此命令。  
  
### 若要支持大纲显示  
  
1.  实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> 语言服务对象上。  
  
2.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 针对当前的大纲显示会话对象，若要添加新的大纲区域。  
  
## 可靠编程  
 当用户选择 **折叠到定义** 上 **大纲显示** 菜单上，IDE 将调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> 语言服务上。  
  
 当调用此方法时，IDE 会将传递在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 指针 （指向文本缓冲区的指针） 和一个 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> （指向当前的大纲显示会话的指针）。  
  
 您可以调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 方法通过指定这些区域中的多个大纲区域 `rgOutlnReg` 参数。`rgOutlnReg` 参数是 <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> 结构。 此过程使你能够指定不同的特征的隐藏区域，如是否展开或折叠某一特定区域。  
  
> [!NOTE]
>  要格外小心隐藏新行字符。 隐藏的文本应将扩展从开始处的第一行到最后一个字符的最后一行的部分，使最后一个新行字符时可见。  
  
## 请参阅  
 [如何︰ 隐藏的文本，在提供支持传统语言服务](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [如何︰ 提供旧语言服务中的扩展大纲显示支持](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)