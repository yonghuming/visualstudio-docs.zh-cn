---
title: "编辑器导入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81e0a131ef35202581ffb78a75a6b48239a7d81f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="editor-imports"></a>编辑器导入
你可以导入大量的编辑器服务、 工厂、 和到核心编辑器将你的扩展提供不同类型的访问的代理。 例如，你可以导入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>若要为你提供<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>为给定的内容类型。 （此导航器情况允许你在文本缓冲区上执行不同类型的搜索）。  
  
 若要使用的编辑器导入，你将其导入作为字段或属性的类的导出 Managed Extensibility Framework 组件部件。  
  
> [!NOTE]
>  有关 Managed Extensibility Framework 的详细信息，请参阅[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。  
  
## <a name="import-syntax"></a>导入语法  
 下面的示例演示如何导入编辑器选项工厂服务。  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 如果你想要作为字段并不是属性导入服务，应将其设置为`null`以避免编译器警告有关不分配给一个变量声明中：  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 使用导入的更多示例，请参阅下面的演练：  
  
 [演练：创建边距字形](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [演练：自定义文本视图](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [演练：突出显示文本](../extensibility/walkthrough-highlighting-text.md)  
  
 [演练：显示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [演练：显示签名帮助](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [演练：显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [演练：显示灯泡建议](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)  
  
## <a name="importing-the-service-provider"></a>导入服务提供程序  
 你还可以导入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>（在程序集中 Microsoft.VisualStudio.Shell.Immutable.10.0 找到） 相同的方式来获取对 Visual Studio 服务的访问：  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 请参阅[演练： 从编辑器扩展访问 DTE 对象](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)有关详细信息。  
  
## <a name="services"></a>服务  
 编辑器服务是通常单个实体提供服务并在多个组件之间共享。  
  
|导入|提供|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|文件扩展名之间的关系和<xref:Microsoft.VisualStudio.Utilities.IContentType>对象。|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 对象的集合。|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> 对象|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|许多编辑器适配器对象：<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>给定的文本视图对象。|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|一个 <xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|一个 <xref:Microsoft.VisualStudio.Text.ITextDocument>。|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>的差异。|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>的差异。|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>或<xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>。|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>为一组<xref:Microsoft.VisualStudio.Text.ITextBuffer>对象。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>为<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>为<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>为<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>为<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|保持的集合<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>对象。|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>文本缓冲区。|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>文本视图。|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>对应于指定范围。|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>文本视图。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>为<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|获取的自动缩进<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>对象。|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|管理<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>为<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|一个 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|从一组的快照范围生成 RTF 格式的文本。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>为<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>用于格式化视图中的文本行。|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>对象<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|搜索文本快照。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>为<xref:Microsoft.VisualStudio.Text.ITextBuffer>通过<xref:Microsoft.VisualStudio.Utilities.IContentType>。|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>文本视图。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|一组标准的标志符号。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>为<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|跟踪键盘处理。|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|标准<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>对象。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|维护文本在缓冲区之间的关系和<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>对象。|  
  
## <a name="other-imports"></a>其他导入  
 提供程序工厂和代理通常是可以在多个组件中有多个实例的实体。  
  
|导入|提供|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>类型的<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) 对于给定的缓冲区。|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|文本标记标记器 (<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>类型的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>)。|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>为给定<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|一个 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|一个 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|一个 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>。|  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)