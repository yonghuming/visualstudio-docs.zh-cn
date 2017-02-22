---
title: "传统语言服务中的语句结束 | Microsoft Docs"
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
  - "语句结束"
  - "语言服务，语句结束"
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 传统语言服务中的语句结束
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

语句结束是依据语言服务可帮助用户完成语言关键字或启动它们都在核心编辑器中键入的元素的过程。 本主题讨论语句完成的工作原理以及如何在您的语言服务中实现它。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现语句完成功能的新方法的详细信息，请参阅 [演练: 显示语句完成](../../extensibility/walkthrough-displaying-statement-completion.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 实现语句结束  
 在核心编辑器中，语句完成后会激活一个特殊的用户界面，更轻松地以交互方式可帮助您并快速编写代码。 语句结束有助于通过显示相关的对象或类时需要它们，这样可以避免您无需记住的特定元素或无需查找帮助参考主题中。  
  
 若要实现语句完成提示，您的语言必须具有语句完成触发器，可以分析。 例如， [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 使用圆点 （.） 运算符，而 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 使用一个箭头 （\-\>\) 运算符。 语言服务可以使用多个触发器来启动语句结束。 在命令筛选器中对这些触发器进行编程。  
  
## 命令筛选器和触发器  
 命令的筛选器拦截触发器或触发器的匹配项。 若要将命令筛选器添加到视图中，实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，并将其附加到该视图通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法。 可以使用相同的命令筛选器 \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) 为您的语言服务，如语句完成、 错误标记和方法的提示的所有方面。 有关详细信息，请参阅[截获旧语言服务命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
 当在编辑器中输入该触发器 — 具体来说，文本缓冲区 — 语言服务然后调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法。 这将导致编辑器以将用户界面，以便用户可以从中选择语句完成候选项。 此方法要求您实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> 作为参数的标志。 完成项目的列表显示在滚动列表框中。 用户继续键入，在列表框中的所选内容会更新以反映最新字符与最接近类型化。 核心编辑器实现 UI 的语句结束，但语言服务必须实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 接口来定义一组语句的候选完成项。  
  
## 请参阅  
 [截获旧语言服务命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)