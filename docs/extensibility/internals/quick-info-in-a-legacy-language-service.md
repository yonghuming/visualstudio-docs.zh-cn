---
title: "在旧语言服务中的快速信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 692884d31e55921489aad0fbbea32ca1c094c6c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="quick-info-in-a-legacy-language-service"></a>在旧语言服务中的快速信息
IntelliSense 快速信息在当用户将插入符号放置在标识符中并选择在源中显示有关标识符的信息**快速信息**从**IntelliSense**菜单或保存鼠标通过标识符的光标。 这将导致出现包含的有关标识符的信息工具提示。 此信息通常包括标识符类型。 活动的调试引擎时，此信息可能包括的当前值。 调试引擎提供表达式值，而该语言服务处理仅标识符。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解详细信息，请参阅[演练： 显示快速信息工具提示](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
 托管的包框架 (MPF) 语言服务类用于显示 IntelliSense 快速信息工具提示提供完全支持。 你所要做的只是提供要显示和启用快速信息功能的文本。  
  
 要显示的文本通过调用获取<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法分析器分析原因值为<xref:Microsoft.VisualStudio.Package.ParseReason>。 此原因是告知分析器获取的类型信息 （或任何适合的快速信息工具提示中显示） 中指定的位置处的标识符<xref:Microsoft.VisualStudio.Package.ParseRequest>对象。 <xref:Microsoft.VisualStudio.Package.ParseRequest>对象是什么传递到<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。  
  
 分析器必须分析中的位置的所有内容<xref:Microsoft.VisualStudio.Package.ParseRequest>以便确定所有标识符的类型的对象。 然后分析器在分析请求位置必须获取的标识符。 最后，分析器必须将传递到该标识符与关联的工具提示数据<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象，以便该对象可以返回从文本<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>方法。  
  
## <a name="enabling-the-quick-info-feature"></a>启用快速信息功能  
 若要启用快速信息功能，必须设置`CodeSense`和`QuickInfo`命名的参数<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。这些属性设置<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>和<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A>属性。  
  
## <a name="implementing-the-quick-info-feature"></a>实现快速信息功能  
 <xref:Microsoft.VisualStudio.Package.ViewFilter>类处理的 IntelliSense 快速信息操作。 当<xref:Microsoft.VisualStudio.Package.ViewFilter>类接收<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令、 类调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法分析原因为<xref:Microsoft.VisualStudio.Package.ParseReason>和时插入符号的位置<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>发送命令。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法分析器必须然后分析到给定位置的源，然后分析中确定要在快速信息工具提示中显示内容的给定位置的标识符。  
  
 大多数分析器执行整个源文件的初始分析，并将结果存储在分析树。 当执行完成分析<xref:Microsoft.VisualStudio.Package.ParseReason>传递给<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。 然后可以在其他类型的分析中使用的分析树以获取所需的信息。  
  
 例如，分析原因值的<xref:Microsoft.VisualStudio.Package.ParseReason>可以找到在源位置的标识符，并在要获取的类型信息的分析树中查找它。 此类型信息随后将传递到<xref:Microsoft.VisualStudio.Package.AuthoringScope>类，并返回<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>方法。