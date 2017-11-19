---
title: "语法着色旧语言服务在 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88af397feba9b06eabd73ec23dcf1204ebe755e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>语法着色中旧语言服务
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用着色服务标识的语言元素，并将它们显示与在编辑器中的指定颜色。  
  
## <a name="colorizer-model"></a>着色器模型  
 该语言服务实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>接口，然后由编辑器。 下图中所示，此实现为语言服务中，从一个单独的对象。  
  
 ![SVC 着色程序图](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
简单的着色器模型  
  
> [!NOTE]
>  语法着色服务是独立于常规[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]着色文本的机制。 有关常规[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]机制支持着色，请参阅[使用字体和颜色](../../extensibility/using-fonts-and-colors.md)。  
  
 除了着色器，该语言服务可以提供由编辑器由它提供可着色的自定义项的广告的自定义可着色项。 你可以执行此操作通过实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>实现对同一对象的接口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>接口。 它将返回自定义可着色项的数目时编辑器调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法，并返回单个自定义可着色数据项时编辑器调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法返回实现的对象<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>接口。 如果该语言服务支持 24 位或高颜色值，它必须实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>作为对同一对象的接口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>接口。  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage 如何使用语言服务着色器  
  
1.  VSPackage 必须获得适当的语言服务，需要语言服务 VSPackage 来执行以下操作：  
  
    1.  使用一个对象，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>接口来获取要被着色的文本。  
  
         文本通常会显示使用的对象来实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口。  
  
    2.  通过查询语言服务 GUID VSPackage 服务提供程序来获取该语言服务。 语言服务在注册表中标识由文件扩展名。  
  
    3.  将关联的语言服务<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>通过调用其<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法。  
  
2.  现在，VSPackage 可以获取，并使用着色器对象，如下所示：  
  
    > [!NOTE]
    >  使用核心编辑器的 Vspackage 无需显式获取一种语言服务的着色器对象。 只要核心编辑器的一个实例获得适当的语言服务，它将执行此处显示的所有着色任务。  
  
    1.  获取语言服务的着色器对象，它实现`T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>接口，通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>语言服务上的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>对象。  
  
    2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法来获取特定范围的着色器信息的文本。  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>返回一个值，一个用于正在着色文本范围中的每个字符数组。 值是由核心编辑器维护的默认着色项列表或自定义着色项列表由语言服务本身维护着色项列表中的索引。  
  
    3.  使用返回的着色信息<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法以显示所选的文本。  
  
> [!NOTE]
>  除了使用语言服务着色器，VSPackage 还可以使用通用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]着色机制的文本。 有关此机制的详细信息，请参阅[使用字体和颜色](../../extensibility/using-fonts-and-colors.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [实现语法着色](../../extensibility/internals/implementing-syntax-coloring.md)  
 讨论如何编辑器访问语言服务的语法颜色设置和语言服务必须实现此方法可以支持语法着色。  
  
 [如何：使用内置的可着色项](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 演示如何使用来自语言服务的内置着色项。  
  
 [自定义可着色项](../../extensibility/internals/custom-colorable-items.md)  
 讨论如何实现自定义可着色的项。  
  
## <a name="see-also"></a>另请参阅  
 [使用字体和颜色](../../extensibility/using-fonts-and-colors.md)