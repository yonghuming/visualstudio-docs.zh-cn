---
title: "提供通过使用旧 API 的语言服务上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 10221f77e65acfb91c625c2f711b5804b64f827e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>提供通过使用旧 API 的语言服务上下文
有两个选项以提供用户上下文中使用的语言服务[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器︰ 提供文本标记的上下文中，也提供所有的用户上下文。 本文概述了每个之间的差异。  
  
 提供到语言服务连接到您自己的编辑器的上下文的详细信息，请参阅[如何︰ 为编辑器提供上下文](../extensibility/how-to-provide-context-for-editors.md)。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>向编辑器中提供文本标记上下文  
 若要为指示文本标记中的编译器错误提供的上下文[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器，请实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>接口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 在此方案中，该语言服务提供上下文，仅当光标位于文本标记上时。 这样，编辑器可以提供到光标位置处关键字**动态帮助**不具有任何属性的窗口。  
  
## <a name="provide-all-user-context-to-the-editor"></a>向编辑器中提供所有的用户上下文  
 如果您要创建的语言服务，并且使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器中，则可以实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>接口，以提供您的语言服务上下文。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 有关实现的`IVsLanguageContextProvider`，上下文包 （集合） 附加到编辑器，它是负责更新上下文包。 当**动态帮助**窗口调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>上空闲时，上下文包在此上下文包接口查询以获取更新的编辑器。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> 编辑器然后通知语言服务，它应更新编辑器中，并将指针传递给上下文包。 这通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>从编辑器到语言服务的方法。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> 上下文包使用指针，该语言服务可以立即添加和删除的特性和关键字。 有关详细信息，请参阅<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>》。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 有两种不同方式实现`IVsLanguageContextProvider`:  
  
-   提供了一个关键字与上下文包  
  
     当调用编辑器更新上下文包时，传递到的相应关键字和属性中，然后返回`S_OK`。 此返回值指示要保留您关键字和特性的上下文，而不是提供对上下文包光标位置处关键字的编辑器。  
  
-   获取从光标位置处关键字的关键字  
  
     当调用编辑器更新上下文包时，传入适当的属性，然后返回`E_FAIL`。 此返回值指示要保留您的属性中的上下文包中，但更新的光标位置处关键字的上下文包的编辑器。  
  
 下图演示了如何实现的语言服务提供上下文`IVsLanguageContextProvider`。  
  
 ![LangServiceImplementation2 图](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
语言服务上下文  
  
 正如您在图中，可以看到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文本编辑器具有附加到它的上下文包。 此上下文包指向三个单独的子上下文包︰ 语言服务、 默认编辑器和文本标记。 语言服务和文本标记子上下文包包含用于该语言服务特性和关键字，如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>接口实现，以及文本标记如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>接口实现。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 如果未实现这些接口之一，编辑器中对默认编辑器子上下文包中光标位置处关键字提供上下文。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>编辑器和设计器的上下文准则  
 设计器和编辑器必须提供的编辑器或设计器窗口的常规关键字。 这样，以便在用户按 F1 时，泛型类型，但适当情况下，帮助主题将显示的设计器或编辑器。 编辑器必须除此之外，提供当前光标位置处关键字或提供根据当前选择的关键术语。 这样做是为了确保指向或当用户按 F1 时，选择显示的文本或 UI 元素帮助主题。 设计器提供了设计器中，如在窗体上的按钮中选定的项的上下文。 编辑器和设计器还必须连接到语言服务中所述[旧语言服务基础知识](../extensibility/internals/legacy-language-service-essentials.md)。
