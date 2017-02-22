---
title: "在早期语言服务中的快速信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "快速信息，支持的语言服务 [托管的包框架]"
  - "IntelliSense、 快速信息"
  - "语言服务 [托管的包框架] 的 IntelliSense 快速信息"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 在早期语言服务中的快速信息
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense 快速信息显示有关标识符的信息源中时用户将光标放在标识符中，选择 **快速信息** 从 **IntelliSense** 菜单或停留在该标识符的鼠标光标。 这将导致出现其中包含有关标识符的信息的工具提示。 此信息通常包含的标识符类型。 如果活动的调试引擎，则此信息可能包括当前值。 调试引擎提供表达式的值，而该语言服务处理仅标识符。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要获得详细信息，请参阅 [演练︰ 显示快速信息工具提示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
 托管的包框架 \(MPF\) 语言服务类用于显示的 IntelliSense 快速信息工具提示提供完全支持。 您需要做的只是提供要显示并启用快速信息功能的文本。  
  
 要显示的文本通过调用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法分析器中的分析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason>。 此通知分析器来获取类型信息 （或任何适于在快速信息工具提示中显示） 中指定的位置处的标识符 <xref:Microsoft.VisualStudio.Package.ParseRequest> 对象。<xref:Microsoft.VisualStudio.Package.ParseRequest> 对象是什么传递给 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。  
  
 分析器必须分析中的位置的所有内容 <xref:Microsoft.VisualStudio.Package.ParseRequest> 对象中以便确定所有标识符的类型。 然后分析器必须分析请求位置处获取的标识符。 最后，分析器必须传递到该标识符与关联的工具提示数据 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 对象，该对象可以返回从文本以便 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 方法。  
  
## 启用快速信息功能  
 若要启用快速信息功能，必须设置 `CodeSense` 和 `QuickInfo` 命名的参数，则 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。设置这些属性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 和 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> 属性。  
  
## 实现快速信息功能  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> 类处理的 IntelliSense 快速信息操作。 当 <xref:Microsoft.VisualStudio.Package.ViewFilter> 类接收 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令，该类会调用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法，分析原因为 <xref:Microsoft.VisualStudio.Package.ParseReason> 和时插入符号的位置 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令已发送。<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法分析器必须然后分析直到到达给定位置的源，然后分析中给定的位置，以确定要在快速信息工具提示中显示的标识符。  
  
 大多数分析器执行整个源文件初始分析，并将结果存储在分析树。 当执行完成分析 <xref:Microsoft.VisualStudio.Package.ParseReason> 传递给 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。 然后，其他类型的分析可用的分析树来获得所需的信息。  
  
 例如，分析原因值的 <xref:Microsoft.VisualStudio.Package.ParseReason> 可以找到在源位置的标识符，并在获取类型信息的分析树中查找它。 此类型信息然后传递给 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 类，并返回 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 方法。