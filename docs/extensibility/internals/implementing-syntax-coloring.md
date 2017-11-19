---
title: "实现语法着色 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d5d251c414c955480d3a7e4289935d913fa470c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-syntax-coloring"></a>实现语法着色
时语言服务提供了语法着色，分析器将一行文本转换为着色的项的数组，并返回与这些着色项对应的令牌类型。 分析器应返回属于可着色项的列表的令牌类型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根据由着色器对象分配给相应的令牌类型的属性的代码窗口中显示每个可着色的项。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不指定分析器接口，并且分析器实现完全由您。 但是，在 Visual Studio 语言包项目提供默认分析器实现。 对于托管代码，托管的包框架 (MPF) 提供对着色文本的完整支持。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解有关实现语法颜色设置的新方式的详细信息，请参阅[演练： 突出显示文本](../../extensibility/walkthrough-highlighting-text.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>跟一个编辑器，为文本着色的步骤  
  
1.  编辑器通过调用获取着色器<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>对象。  
  
2.  编辑器调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>方法来确定着色器是否需要着色器外部维护每个行的状态。  
  
3.  如果着色器需要着色器外部维护的状态，编辑器调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>方法以获取第一个行的状态。  
  
4.  对于每个缓冲区中的行，编辑器调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，用于执行以下步骤：  
  
    1.  文本行传递到扫描程序将文本转换为令牌中。 每个令牌指定令牌的文本和令牌的类型。  
  
    2.  令牌类型转换为可着色项列表的索引。  
  
    3.  令牌的信息用于填充数组中，以便该数组的每个元素对应于在行中的字符。 数组中存储的值可着色项列表中的索引。  
  
    4.  针对每个行返回的行末尾处的状态。  
  
5.  如果着色器要求的状态来维护，编辑器将缓存行的状态。  
  
6.  编辑器中呈现的使用从返回的信息的文本行<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法。 这需要执行以下步骤：  
  
    1.  对于行中每个字符，可以获取的着色的项索引。  
  
    2.  如果使用默认着色项，访问编辑器的可着色项列表。  
  
    3.  否则，调用该语言服务<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法来获取着色的项。  
  
    4.  使用中的着色的项的信息显示呈现文本。  
  
## <a name="managed-package-framework-colorizer"></a>托管的包框架着色器  
 托管的包框架 (MPF) 提供实现着色程序所需的所有类。 语言服务类应该继承<xref:Microsoft.VisualStudio.Package.LanguageService>类，实现所需的方法。 必须通过实现提供扫描仪和分析器<xref:Microsoft.VisualStudio.Package.IScanner>接口，并返回从该接口的实例<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法 (必须在中实现的方法之一<xref:Microsoft.VisualStudio.Package.LanguageService>类)。 有关详细信息，请参阅[旧语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 使用内置可着色项](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自定义可着色项](../../extensibility/internals/custom-colorable-items.md)   
 [开发旧语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [旧版语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)