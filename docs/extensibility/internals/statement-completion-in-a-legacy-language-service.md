---
title: "在旧语言服务中的语句结束 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c694295c3456accc8d2c1cd3b0a1ec20f59343c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="statement-completion-in-a-legacy-language-service"></a>在旧语言服务中的语句结束
语句结束是依据语言服务可帮助用户完成语言关键字或它们已启动在核心编辑器中键入的元素的过程。 本主题讨论语句完成的工作原理以及如何在你的语言服务中实现它。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现语句结束的新方式的详细信息，请参阅[演练： 显示语句结束](../../extensibility/walkthrough-displaying-statement-completion.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="implementing-statement-completion"></a>实现语句结束  
 在核心编辑器中，语句完成后会激活的特殊的用户界面，可更轻松地以交互方式可帮助你和快地编写代码。 语句结束有助于通过显示相关对象或类在需要时这会避免你无需记住的特定元素或无需查找帮助参考主题中。  
  
 若要实现语句完成，你的语言必须具有可以分析语句完成触发器。 例如，[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]使用点 （.） 运算符，而[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]使用箭头 （->) 运算符。 语言服务可以使用多个触发器来启动语句结束。 命令筛选器中对这些触发器进行编程。  
  
## <a name="command-filters-and-triggers"></a>命令筛选器和触发器  
 命令的筛选器截获触发器或触发器的匹配项。 若要将命令筛选器添加到视图中，实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口，并将其附加到该视图，通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。 您可以使用相同的命令筛选 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 的你的语言服务，如语句完成、 错误标记和方法提示的所有方面。 有关详细信息，请参阅[截获旧语言服务命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
 当在编辑器中输入该触发器-具体而言，文本缓冲区-语言服务然后调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法。 这将导致编辑器弹出用户界面，以便用户可以选择从语句完成候选项。 此方法要求你实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>和<xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags>标志作为参数。 滚动列表框中显示的完成项的列表。 用户继续键入，在列表框中选择会更新以反映最新的字符与最接近类型。 核心编辑器实现用于语句完成、 UI 但语言服务必须实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>接口可定义一组语句的候选完成项。  
  
## <a name="see-also"></a>另请参阅  
 [截获旧版语言服务命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)