---
title: "通过使用旧版 API 提供的语言服务上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79f58bf66e5d0a137738d0a2cc90f67a287246dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>通过使用旧版 API 提供的语言服务上下文
为要提供用户上下文使用的语言服务的两个选项[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器： 提供文本标记的上下文，或提供所有的用户上下文。 本文概述了每个方面的差异。  
  
 提供到语言服务连接到您自己的编辑器的上下文的详细信息，请参阅[如何： 提供上下文为编辑器](../extensibility/how-to-provide-context-for-editors.md)。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>到编辑器中提供文本标记上下文  
 若要为由文本标记中的编译器错误提供的上下文[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>接口。 在此方案中，语言服务在光标位于在文本标记上时，仅提供上下文。 这允许提供到光标位置处关键字编辑器**动态帮助**不具有任何属性窗口。  
  
## <a name="provide-all-user-context-to-the-editor"></a>提供到编辑器的所有用户上下文  
 如果你要创建语言服务并将[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器中，然后你可以实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>接口来为你的语言服务提供的上下文。  
  
 用于实现的`IVsLanguageContextProvider`，上下文包 （集合） 附加到编辑器中，它负责更新上下文包。 当**动态帮助**窗口调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>上空闲时，上下文包在此上下文包接口查询更新的编辑器。 编辑器然后通知语言服务，它应更新编辑器，并将指针传递给上下文包。 这可通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>从编辑器到语言服务的方法。 到上下文包使用的指针，该语言服务可以现在添加和删除特性和关键字。 有关更多信息，请参见<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。  
  
 有两种不同方式实现`IVsLanguageContextProvider`:  
  
-   提供到上下文包关键字  
  
     当编辑器调用以更新上下文包时，传入的相应关键字和属性，然后返回`S_OK`。 此返回值指示要保留关键字和特性上下文而不提供到上下文包光标位置处关键字的编辑器。  
  
-   获取从光标位置处关键字的关键字  
  
     当编辑器调用以更新上下文包时，传入适当的属性，然后返回`E_FAIL`。 此返回值指示要保留在上下文包中，你的特性，但更新上下文包使用的光标位置处关键字的编辑器。  
  
 下图演示如何实现语言服务提供上下文`IVsLanguageContextProvider`。  
  
 ![LangServiceImplementation2 图](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
语言服务上下文  
  
 正如在图中，您可以看到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文本编辑器具有上下文包附加到它。 此上下文包指向三个单独的子上下文包： 语言服务、 默认编辑器和文本标记。 语言服务和文本标记子上下文包包含特性和关键字语言服务，如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>接口实现，和文本标记如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>接口实现。 如果未实现这些接口之一，然后该编辑器还提供上下文的默认编辑器子上下文包光标位置处关键字。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>编辑器和设计器的上下文准则  
 设计器和编辑器必须提供编辑器或设计器窗口的常规关键字。 因此，当用户按 F1 时，泛型类型，但适当情况下，帮助主题都会显示设计器或编辑器，则是完成此操作。 编辑器必须除此之外，提供当前光标位置处关键字或提供对当前选定内容基于关键术语。 这样做是为了确保指向或在用户按 F1 时选择显示的文本或 UI 元素帮助主题。 设计器提供了在设计器中，例如窗体上的按钮中选定项的上下文。 编辑器和设计器还必须连接到语言服务中所述[旧语言服务 Essentials](../extensibility/internals/legacy-language-service-essentials.md)。