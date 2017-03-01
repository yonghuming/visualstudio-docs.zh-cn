---
title: "编辑器中导入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 19
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 2c7daddb7cd40dd0e5d24f01df141ce30ba713f9
ms.lasthandoff: 02/22/2017

---
# <a name="editor-imports"></a>编辑器中导入
您可以导入大量的编辑器服务、 工厂和分销商，以提供不同类型的访问您的扩展到核心编辑器。 例如，您可以导入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>若要将为您提供<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>对于给定的内容类型。</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> （此导航器允许您对文本缓冲区执行不同类型的搜索。）  
  
 若要使用的编辑器中导入，您作为导入它的字段或属性导出 Managed Extensibility Framework 组件部件的类。  
  
> [!NOTE]
>  有关托管可扩展性框架的详细信息，请参阅[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
## <a name="import-syntax"></a>导入语法  
 下面的示例演示如何导入编辑器选项工厂服务。  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 如果您想要作为一个字段而不是属性导入服务，应将其设置为`null`以避免编译器警告有关未分配给一个变量声明中︰  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 通过导入更多示例，请参阅下面的演练︰  
  
 [演练︰ 创建边缘字形](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [演练︰ 自定义文本视图](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [演练︰ 突出显示文本](../extensibility/walkthrough-highlighting-text.md)  
  
 [演练︰ 显示快速信息工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [演练︰ 显示签名帮助](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [演练：显示语句完成](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [演练：显示智能标记](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>导入的服务提供程序  
 您还可以导入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>（位于程序集 Microsoft.VisualStudio.Shell.Immutable.10.0） 相同的方式来获取对 Visual Studio 服务的访问︰</xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 请参阅[演练︰ 从编辑器扩展访问 DTE 对象](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)有关详细信息。  
  
## <a name="services"></a>服务  
 编辑器服务是提供一种服务，在多个组件之间共享的通常单个实体。  
  
|导入|提供了|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService></xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|文件扩展名之间的关系和<xref:Microsoft.VisualStudio.Utilities.IContentType>对象。</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService></xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|集合<xref:Microsoft.VisualStudio.Utilities.IContentType>对象。</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService></xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>对象</xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService></xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|许多编辑器适配器对象︰<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService></xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>为给定的文本视图对象。</xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService></xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextBuffer>.</xref:Microsoft.VisualStudio.Text.ITextBuffer>|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService></xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextDocument>.</xref:Microsoft.VisualStudio.Text.ITextDocument>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>的差异。</xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>的差异。</xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>或<xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.</xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>的一套<xref:Microsoft.VisualStudio.Text.ITextBuffer>对象。</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>为一种<xref:Microsoft.VisualStudio.Text.ITextBuffer>。</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>为一种<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>为一种<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>为一种<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|集合进行维护<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>对象。</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>文本缓冲区。</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>为文本视图。</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>对应于指定范围。</xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>为文本视图。</xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>为一种<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|获取自动缩进<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>对象。</xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService></xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|将管理<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>的一种<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.</xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService></xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|从快照范围的一组生成 RTF 格式的文本。|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> <xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|一个<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>进行格式化视图中的文本行。</xref:System.Windows.Media.TextFormatting.TextParagraphProperties>|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService></xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> <xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView>对象</xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService></xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|搜索文本快照。|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService></xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>为<xref:Microsoft.VisualStudio.Text.ITextBuffer>通过<xref:Microsoft.VisualStudio.Utilities.IContentType>。</xref:Microsoft.VisualStudio.Utilities.IContentType> </xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService></xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>为文本视图。</xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService></xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|一组标准的标志符号。|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService></xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>为一种<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService></xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|跟踪键盘处理。|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService></xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|标准<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>对象。</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry></xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|维护文本缓冲区之间的关系和<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>对象。</xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>|  
  
## <a name="other-imports"></a>其他导入  
 提供程序工厂和代理通常是可以在多个组件中有多个实例的实体。  
  
|导入|提供了|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>类型的<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) 对于给定的缓冲区。</xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|文本标记 (<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>类型的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>)。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>对于给定的<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker></xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>|  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)
