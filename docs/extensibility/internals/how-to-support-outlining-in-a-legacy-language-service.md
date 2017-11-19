---
title: "如何： 支持旧语言服务中的大纲显示 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e08ca6d5a670bb2c1a0f0073920c753add50322c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>如何： 支持旧语言服务中的大纲显示
以大纲方式显示用于展开或折叠的文本的不同区域。 方式大纲显示使用不同的语言可以以不同方式定义。 有关详细信息，请参阅[大纲显示](../../ide/outlining.md)。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现以大纲方式显示的新方式的详细信息，请参阅[演练： 以大纲方式显示](../../extensibility/walkthrough-outlining.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
 下面演示如何为你的语言服务支持此命令。  
  
### <a name="to-support-outlining"></a>若要支持大纲显示  
  
1.  实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>你语言的服务对象。  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>上当前的大纲显示会话对象，若要添加新的大纲区域。  
  
## <a name="robust-programming"></a>可靠编程  
 当用户选择**折叠到定义**上**大纲**菜单中，在 IDE 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>语言服务上。  
  
 当调用此方法时，IDE 将传递中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>指针 （指向文本缓冲区的指针） 和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>（指向当前的大纲显示会话的指针）。  
  
 你可以调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>方法通过指定这些区域中的多个大纲区域`rgOutlnReg`参数。 `rgOutlnReg`参数是<xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>结构。 此过程使你能够指定不同的特征的隐藏区域，如某一特定区域是展开还是折叠。  
  
> [!NOTE]
>  请谨慎使用隐藏新行字符。 隐藏的文本应将扩展从第一个行的开头到最后一个字符的部分中，仅显示最后一个新行字符的最后一行。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 隐藏的文本在提供支持，旧语言服务](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [如何：提供旧版语言服务中扩展的大纲显示支持](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)