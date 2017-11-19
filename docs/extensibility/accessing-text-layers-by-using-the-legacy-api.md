---
title: "通过使用旧版 API 访问文本层 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54a981a57605ccb93062ac0678b1e8b5673c6d1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>通过使用旧版 API 访问文本层
文本层通常封装文本布局的某些方面。 例如，"函数的每一次的"层隐藏的文本之前和之后包含脱字号 （文本插入点） 的函数。  
  
 文本层驻留之间缓冲区和视图，并修改该视图可以看到缓冲区的内容的方式。  
  
## <a name="text-layer-information"></a>文本层信息  
 以下列表描述文本层中的工作原理[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   可以使用语法颜色设置和标记修饰文本层中的文本。  
  
-   当前不能实现您自己的层。  
  
-   层公开<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，该类派生自<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>。 作为一个层，使我们能够考察以多态方式处理基础层还实现本身的文本缓冲区。  
  
-   在视图和缓冲区之间可能位于任意数目的层。 每个层仅处理获得它，下面的层和视图很大程度上处理的最顶层的层。 （视图不必缓冲区有关的一些信息。）  
  
-   层可能会影响其下面的层。 它不会影响超出发起标准事件它上面的层。  
  
-   在编辑器中，隐藏的文本、 综合文本和自动换行作为层实现。 你可以实现隐藏和综合文本，而无需直接与层交互。 有关详细信息，请参阅[旧语言服务中的大纲显示](../extensibility/internals/outlining-in-a-legacy-language-service.md)和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>。  
  
-   每个文本层都有其自己本地的坐标系统，通过公开<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>接口。 换行层，例如，可能包含两行，而基础的文本缓冲区可能包含只有一个行。  
  
-   该视图通信层通过<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>接口。 使用此接口进行对帐缓冲区坐标视图坐标。  
  
-   任何层如来源文本的综合文本层必须提供的本地实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>。  
  
-   除了<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，文本层必须实现<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>并激发中的事件<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>接口。  
  
## <a name="see-also"></a>另请参阅  
 [语法着色中自定义编辑器](../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用文本标记用于旧 API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [使用旧版 API 自定义编辑器控件和菜单](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)