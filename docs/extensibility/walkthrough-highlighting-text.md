---
title: "演练︰ 突出显示文本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 42
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
ms.openlocfilehash: 029cc7785c49a08c7128bfaaff8f236e438efad8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-highlighting-text"></a>演练︰ 突出显示文本
通过创建托管可扩展性框架 (MEF) 部件的组件，可以将不同的视觉效果添加到编辑器。 本演练演示如何突出显示当前的单词在文本文件中每个匹配项。 如果单词在文本文件中出现不止一次，并且在一个匹配项中定位脱字号，将突出显示每个匹配项。  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`HighlightWordTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
## <a name="defining-a-textmarkertag"></a>定义 TextMarkerTag  
 突出显示文本的第一步是子类化<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>并定义其外观。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>若要定义 TextMarkerTag 和 MarkerFormatDefinition  
  
1.  添加一个类文件并将其命名**HighlightWordTag**。  
  
2.  添加以下引用︰  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  导入以下命名空间。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4.  创建一个类，继承自<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>并将其命名`HighlightWordTag`。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
    ```c#  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  创建第二个类，该类继承<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>，并将其命名为 HighlightWordFormatDefinition。</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 若要使用此格式定义为你的标记，必须将其导出具有以下属性︰  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 标记用于引用此格式</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>︰ 这将导致要在 UI 中显示的格式</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
    ```c#  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  在 HighlightWordFormatDefinition 的构造函数，定义其显示名称和外观。 Background 属性定义的填充颜色，而的前景色属性定义的边框颜色。  
  
    ```c#  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  在 HighlightWordTag 的构造函数，传入刚刚创建的格式定义的名称。  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>实现 ITagger  
 下一步是实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>接口。</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 此接口分配，对给定的文本缓冲区、 提供文本突出显示的标记和其他视觉效果。  
  
#### <a name="to-implement-a-tagger"></a>若要实现标记  
  
1.  创建一个类以实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>类型的`HighlightWordTag`，并将其命名`HighlightWordTagger`。</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
    ```c#  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  将以下私有字段和属性添加到类︰  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>，对应于当前的文本视图。</xref:Microsoft.VisualStudio.Text.Editor.ITextView>  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>，它对应于文本视图基础的文本缓冲区。</xref:Microsoft.VisualStudio.Text.ITextBuffer>  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>，用于查找的文本。</xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>，其中具有用于导航文本范围内的方法。</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>  
  
    -   一个<xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>，该类包含一组字以将突出显示。</xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>  
  
    -   一个<xref:Microsoft.VisualStudio.Text.SnapshotSpan>，它对应于当前的单词。</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
    -   一个<xref:Microsoft.VisualStudio.Text.SnapshotPoint>，这对应于当前插入符号的位置。</xref:Microsoft.VisualStudio.Text.SnapshotPoint>  
  
    -   锁定对象。  
  
    ```c#  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  添加一个构造函数初始化前面列出的属性并添加<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>事件处理程序。</xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4.  事件处理程序都调用`UpdateAtCaretPosition`方法。  
  
    ```c#  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5.  您还必须添加`TagsChanged`update 方法将调用的事件。  
  
     [!code-cs[VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs) ] 
     [!code-vb [VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  `UpdateAtCaretPosition()`方法等同于 word 光标位于何地构造一个列表的文本缓冲区中找到的每个词<xref:Microsoft.VisualStudio.Text.SnapshotSpan>对象相对应的单词的出现次数。</xref:Microsoft.VisualStudio.Text.SnapshotSpan> 然后，它调用`SynchronousUpdate`，这会引发`TagsChanged`事件。  
  
    ```c#  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  `SynchronousUpdate`对执行同步更新`WordSpans`和`CurrentWord`属性，并引发`TagsChanged`事件。  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8.  您必须实现<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法。</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 此方法采用集合<xref:Microsoft.VisualStudio.Text.SnapshotSpan>对象，并返回的标记范围的枚举。</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
     在 C# 中实现此方法作为 yield 迭代器，从而使迟缓计算 （即，仅当访问单个项集的评估） 的标记。 在 Visual Basic 中将标记添加到列表并返回的列表。  
  
     该方法将返回此处<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>对象，它具有"蓝色" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>，该属性提供背景为蓝色。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>  
  
    ```c#  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>创建标记提供程序  
 若要创建您的标记，则必须实现一种<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>。</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> 此类是 MEF 组件部件，因此你必须设置正确的属性，以便识别此扩展插件。  
  
> [!NOTE]
>  有关 MEF 的详细信息，请参阅[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
#### <a name="to-create-a-tagger-provider"></a>若要创建标记提供程序  
  
1.  创建一个名为类`HighlightWordTaggerProvider`实现<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>，并将其导出与<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>  
  
    ```c#  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  您必须导入两个编辑器服务，<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>和<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、 来实例化标记。</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> </xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    ```c#  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  实现<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>方法返回的实例`HighlightWordTagger`。</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>  
  
    ```c#  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 HighlightWordTest 解决方案并在实验实例中运行它。  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>若要生成并测试 HighlightWordTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件，并键入一些文本，在其中重复出现的单词，例如，"你好你好你好"。  
  
4.  将光标置于"你好"的匹配项之一。 每个匹配项应以蓝色突出显示。  
  
## <a name="see-also"></a>另请参阅  
 [演练︰ 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
