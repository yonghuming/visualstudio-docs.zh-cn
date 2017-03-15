---
title: "实现功能︰ 语法着色 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
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
ms.openlocfilehash: 67535bcc2c907978c24d764c617f8311dc51a444
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-syntax-coloring"></a>实现功能︰ 语法着色
语言服务提供语法颜色设置后，分析器将一行文本转换为可着色的项的数组，并返回对应于这些可着色的项的令牌类型。 分析器应返回属于可着色的项的列表的令牌类型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根据分配给相应的标记类型的着色器对象的属性的代码窗口中显示每个可着色的项。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]未指定使用分析器的接口，并解析器实现方式完全由您决定。 但是，在 Visual Studio 语言包项目中提供的默认解析器实现。 对于托管代码，托管的包框架 (MPF) 为着色文本提供完整支持。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要了解有关实现语法突出显示的新方法的详细信息，请参阅[演练︰ 突出显示文本](../../extensibility/walkthrough-highlighting-text.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>后跟一个编辑器，为文本着色的步骤  
  
1.  编辑器中获取着色器通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>对象。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>  
  
2.  编辑器调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>方法，以确定是否着色器需要着色器外部维护每条线的状态。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>  
  
3.  如果着色器需要着色器外部维护的状态，编辑器将调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>方法来获取第一个行的状态。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>  
  
4.  对于每个缓冲区中的行，编辑器调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，后者将执行以下步骤︰</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    1.  文本行传递给扫描仪将文本转换为标记。 每个标记指定的令牌文本和标记类型。  
  
    2.  标记类型转换为可着色的项列表中的索引。  
  
    3.  令牌信息用于填充数组中，这样，该数组的每个元素对应于在行中的字符。 数组中存储的值是为可着色的项列表的索引。  
  
    4.  为每一行返回行结尾处的状态。  
  
5.  如果着色器需要维护状态，编辑器将缓存行的状态。  
  
6.  编辑器中呈现文本使用从返回的信息的一行<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 这需要执行以下步骤：  
  
    1.  在行中的每个字符，获取可着色的项索引。  
  
    2.  如果使用的默认可着色的项，请访问的编辑器可着色的项列表。  
  
    3.  否则，调用该语言服务<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法以获取可着色的项。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>  
  
    4.  使用可着色的项中的信息来显示呈现文本。  
  
## <a name="managed-package-framework-colorizer"></a>托管的包 Framework 着色器  
 托管的包框架 (MPF) 提供了实现着色器所需的所有类。 您的语言服务类应该继承<xref:Microsoft.VisualStudio.Package.LanguageService>类，实现所需的方法。</xref:Microsoft.VisualStudio.Package.LanguageService> 您必须通过实现提供扫描器和分析器<xref:Microsoft.VisualStudio.Package.IScanner>接口，并返回从该接口的实例<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法 (一种方法，必须在实现<xref:Microsoft.VisualStudio.Package.LanguageService>类)。</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner> 有关详细信息，请参阅[旧语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何︰ 使用内置可着色的项](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自定义可着色的项](../../extensibility/internals/custom-colorable-items.md)   
 [开发旧语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [在早期语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
