---
title: "在编辑器内 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: "31"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1876f334ad1b444b464ecc420767dea90baed6b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="inside-the-editor"></a>在编辑器内
编辑器由组成大量的其他子系统，旨在使编辑器文本模型单独从文本视图和用户界面。  
  
 下列各节介绍编辑器的不同方面：  
  
-   [子系统的概述](../extensibility/inside-the-editor.md#overview)  
  
-   [文本模型](../extensibility/inside-the-editor.md#textmodel)  
  
-   [文本视图](../extensibility/inside-the-editor.md#textview)  
  
 下列各节介绍编辑器的功能：  
  
-   [标记和分类器](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [修饰](../extensibility/inside-the-editor.md#adornments)  
  
-   [投影](../extensibility/inside-the-editor.md#projection)  
  
-   [大纲显示](../extensibility/inside-the-editor.md#outlining)  
  
-   [鼠标绑定](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [编辑器操作](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a>子系统的概述  
  
### <a name="text-model-subsystem"></a>文本模型子系统  
 文本模型子系统负责表示文本并启用其操作。 文本模型子系统包含<xref:Microsoft.VisualStudio.Text.ITextBuffer>接口，描述由编辑器显示的字符序列。 此文本可以修改、 跟踪，并且其他操作在许多方面。 文本模型还提供有关以下方面的类型：  
  
-   将文本相关联的文件，并管理读取和写入其文件系统中的服务。  
  
-   查找的对象的两个序列之间的最小差异的一种差异服务。  
  
-   一个系统，用于描述方面的其他缓冲区中的文本子集缓冲区中的文本。  
  
 文本模型子系统是免费的用户界面 (UI) 概念。 例如，不负责文本格式设置或文本布局，并且它有可能与文本相关联的 visual 修饰不知道。  
  
 Microsoft.VisualStudio.Text.Data.dll 和 Microsoft.VisualStudio.CoreUtilitiy.dll，仅取决于.NET Framework 基类库和 Managed Extensibility Framework (MEF) 中包含的文本模型子系统的公共类型。  
  
### <a name="text-view-subsystem"></a>文本视图子系统  
 文本视图子系统负责格式设置和显示文本。 此子系统中的类型分为两个图层，具体取决于是否类型依赖 Windows Presentation Foundation (WPF)。 最重要的类型为<xref:Microsoft.VisualStudio.Text.Editor.ITextView>和<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>，该控制要显示的文本行组和还脱字号、 所选内容，并且用于通过使用 WPF UI 元素装饰文本的功能。 此子系统还提供了将文本环绕边距显示区域。 这些边距可以进行扩展，并且可以包含不同类型的内容和视觉效果。 边距的示例包括行号显示和滚动条。  
  
 Microsoft.VisualStudio.Text.UI.dll 和 Microsoft.VisualStudio.Text.UI.Wpf.dll 中包含的文本视图子系统的公共类型。 第一个程序集包含独立于平台的元素，而第二个包含特定于 WPF 的元素。  
  
### <a name="classification-subsystem"></a>分类子系统  
 分类子系统负责确定文本的字体属性。 分类器将文本分解成不同的类，例如，"关键字"或"注释"。 分类格式映射与这些类实际字体属性，例如，"蓝色 Consolas 10 pt"。 格式和呈现文本时，将文本视图通过使用此信息。 标记，本主题中后面的更多详细信息中所述启用要与的文本范围关联的数据。  
  
 分类子系统的公共类型都包含在 Microsoft.VisualStudio.Text.Logic.dll，并且他们与分类，其包含在 Microsoft.VisualStudio.Text.UI.Wpf.dll 可视方面交互方式。  
  
### <a name="operations-subsystem"></a>操作子系统  
 操作子系统定义编辑器行为。 它提供了 Visual Studio 编辑器命令的实现和撤消系统。  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>进一步查看文本模型和文本视图  
  
###  <a name="textmodel"></a>文本模型  
 文本模型子系统包括不同类型的文本的分组。 其中包括文本缓冲区、 文本快照和文本段。  
  
#### <a name="text-buffers-and-text-snapshots"></a>文本缓冲区和文本快照  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>接口表示通过使用 utf-16，这是使用的编码进行编码的 Unicode 字符序列`String`.NET Framework 中的类型。 文本缓冲区可以保存为文件系统文档，但这不是必需。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>用于创建一个空文本的缓冲区或从字符串或从初始化文本缓冲区<xref:System.IO.TextReader>。 文本缓冲区可以保存到文件系统为<xref:Microsoft.VisualStudio.Text.ITextDocument>。  
  
 任何线程可以编辑文本缓冲区，直到一个线程通过调用采用的文本缓冲区所有权<xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>。 之后，只有该线程可以执行编辑。  
  
 在其生存期内，文本缓冲区可以通过许多版本。 每次在编辑缓冲区，以及对不可变生成新版本<xref:Microsoft.VisualStudio.Text.ITextSnapshot>表示该版本的缓冲区的内容。 由于文本快照是不可变的你可以访问而没有限制的任何线程上的文本快照，即使它表示的文本缓冲区不断更改。  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>文本快照和文本快照行  
 为字符序列或行的序列，你可以查看文本快照的内容。 字符和行都是同时索引从零开始。 一个空文本快照包含零个字符和一个空的行。 一条线分隔的任意有效 Unicode 换行字符序列，或通过的开头或末尾的缓冲区。 换行字符显式表示文本快照中并不是所有具有相同文本快照中的换行符。  
  
> [!NOTE]
>  有关在 Visual Studio 编辑器中的行中断符的详细信息，请参阅[编码和换行符](../ide/encodings-and-line-breaks.md)。  
  
 文本行由<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>对象，可以获取从文本快照为特定的行号或特定的字符位置。  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints、 SnapshotSpans 和 NormalizedSnapshotSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.SnapshotPoint>表示在快照中的字符位置。 保证位置都介于零和快照的长度。 A<xref:Microsoft.VisualStudio.Text.SnapshotSpan>表示在快照中的文本范围。 保证其末尾的位置都介于零和快照的长度。 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>包含的一组<xref:Microsoft.VisualStudio.Text.SnapshotSpan>从同一个快照的对象。  
  
#### <a name="spans-and-normalizedspancollections"></a>范围和 NormalizedSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.Span>表示可以应用于文本快照中的文本范围的间隔。 快照位置是从零开始的因此范围可以同时包括零的任何位置启动。 `End`属性的一段等于的总和其`Start`属性并将其`Length`属性。 A`Span`不包括按编制索引的字符`End`属性。 例如，具有的起始范围 = 5 和长度 = 3 已结束 = 8，它包括在位置 5、 6 和 7 个字符。 在这段的表示法是 5..8）。  
  
 这两个范围相交如果它们具有任何共同的位置，包括的结束位置。 因此的交集 [3, 5) 和 [2, 7) 是 [3, 5) 以及的交集 [3, 5) 和 [5, 7) 是 [5，5）。 (请注意，[5，5) 是空的范围。)  
  
 如果它们具有共同的位置，在结束位置除外，这两个范围重叠。 空的跨度永远不会重叠任何其他范围，且这两个范围的重叠永远不会为空。  
  
 A<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>是范围的范围的开始属性顺序的列表。 在列表中，合并重叠或相邻的范围。 例如，给定的一套跨度 [5..9)，[0..1)，[3..6)，和 [9..10)，规范化的列表的范围是 [0..1)，[3..10)。  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit、 TextVersion 和文本更改通知  
 可以使用更改的文本缓冲区内容<xref:Microsoft.VisualStudio.Text.ITextEdit>对象。 创建此类对象 (通过使用之一`CreateEdit()`方法<xref:Microsoft.VisualStudio.Text.ITextBuffer>) 启动文本事务组成的文本编辑。 每个编辑是文本的由字符串缓冲区中某些范围的替代。 坐标和内容的每个编辑相对于来表示缓冲区的快照事务开始时。 <xref:Microsoft.VisualStudio.Text.ITextEdit>对象调整受同一事务中的其他编辑的编辑的坐标。  
  
 例如，考虑包含此字符串的文本缓冲区：  
  
```  
abcdefghij  
```  
  
 应用事务，其中包含两个编辑、 替换在范围的一个编辑 [2..4) 使用的字符`X`并替换在跨度第二个编辑 [6..9) 使用的字符`Y`。 结果为此缓冲区：  
  
```  
abXefYj  
```  
  
 第二个编辑的坐标相对于事务，开头缓冲区的内容应用第一个编辑之前计算。  
  
 对缓冲区进行的更改生效时<xref:Microsoft.VisualStudio.Text.ITextEdit>对象提交通过调用其`Apply()`方法。 如果没有至少一个非空编辑，新<xref:Microsoft.VisualStudio.Text.ITextVersion>创建一个新<xref:Microsoft.VisualStudio.Text.ITextSnapshot>创建，且一个`Changed`引发事件。 每个文本版本具有不同文本快照。 文本快照后编辑事务，表示文本缓冲区的完成状态，但文本版本描述仅从一个快照更改到下一步。 通常情况下，文本快照并打算使用一次，则丢弃，而文本版本必须始终保持有效了一段时间。  
  
 文本版本包含<xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>。 此集合描述所做的更改，应用于快照时，将生成后续的快照。 每个<xref:Microsoft.VisualStudio.Text.ITextChange>集合中包含的更改，替换的字符串，并替换字符串的字符位置。 被替换的字符串为空基本插入，并且替换字符串是为基本删除空。 规范化的集合始终是`null`文本缓冲区的最新版本。  
  
 只有一个<xref:Microsoft.VisualStudio.Text.ITextEdit>可以实例化对象的文本缓冲区在任何时候，并且必须拥有文本缓冲区 （如果已声明所有权） 的线程上执行所有文本编辑。 可以通过调用放弃文本编辑其`Cancel`方法或其`Dispose`方法。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>此外提供了`Insert()`， `Delete()`，和`Replace()`方法类似于在上找到<xref:Microsoft.VisualStudio.Text.ITextEdit>接口。 调用这些具有相同的效果与创建<xref:Microsoft.VisualStudio.Text.ITextEdit>对象，进行类似的调用，，然后将应用编辑。  
  
#### <a name="tracking-points-and-tracking-spans"></a>跟踪点和跟踪范围  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint>表示文本缓冲区中的字符位置。 如果缓冲区中引起要移动的字符的位置的方式进行编辑，跟踪点会转而使用它。 例如，如果跟踪点是指位置 10 在缓冲区中，并且在缓冲区的开头插入五个字符，跟踪点然后指位置 15。 如果插入的操作发生在精确地表示跟踪点的位置，其行为由其<xref:Microsoft.VisualStudio.Text.PointTrackingMode>，这可以是`Positive`或`Negative`。 如果跟踪模式为正，跟踪点是指同一字符，现在位于末尾插入;如果跟踪模式为负，跟踪点是指原始位置插入第一个字符。 如果删除由跟踪点位置处的字符，则跟踪点将在后面已删除的范围的第一个字符中下移。 例如，如果跟踪点是指位置 5，处的字符，并且删除位置 3 到 6 个字符，跟踪点是指位置 3 处的字符。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan>代表一系列的字符而不是只在一个位置。 其行为由其<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>。 如果范围跟踪模式为<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，跟踪范围增长 span 跟踪模式是将文本插入到其边缘; <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，跟踪范围未包含在其边缘处插入的文本。 但是，如果范围跟踪模式为<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，插入将当前位置推送接近开始时，如果范围跟踪模式<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，插入推送当前结束位置。  
  
 可以获取文本缓冲区到其所属的任何快照的跟踪点的位置或跟踪范围的跨度。 跟踪点和跟踪范围可以安全地引用从任意线程。  
  
#### <a name="content-types"></a>内容类型  
 内容类型是内容的一种机制，用于定义不同类型。 内容类型可以是文件类型，如"text"、"代码"或"binary"或"xml"、"vb"或"c#"等的技术类型。 例如，word"using"是在 C# 和 Visual Basic 中，但不是在其他编程语言的关键字。 因此，此关键字的定义可能限制为"c#"和"vb"内容类型。  
  
 内容类型用作筛选器修饰和编辑器的其他元素。 许多编辑器功能和扩展点定义每个内容类型;例如，文本着色与不同纯文本文件、 XML 文件和 Visual Basic 源代码文件。 创建，并且可以更改文本缓冲区的内容类型时，文本缓冲区通常会被分配的内容类型。  
  
 内容类型可以多个-继承其他内容类型。 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>允许您为给定的内容类型的父指定多个基类型。  
  
 开发人员可以定义自己的内容类型和使用注册<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>。 许多编辑器功能可通过使用相对于特定的内容类型定义<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>。 例如，编辑器边距、 修饰和鼠标处理程序可以定义，以便它们仅适用于显示特定内容类型的编辑器。  
  
###  <a name="textview"></a>文本视图  
 模型视图控制器 (MVC) 模式的视图部分定义的视图，如在滚动条和插入符号的图形元素格式的文本视图。 Visual Studio 编辑器中的所有表示法元素基于 WPF。  
  
#### <a name="text-views"></a>文本视图  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>接口是独立于平台的表示形式的文本视图。 它主要用于在窗口中，显示文本文档，但它还可用于其他目的，例如，在工具提示。  
  
 文本视图引用不同类型的文本缓冲区。 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>属性是指<xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel>指向这些三个不同的文本缓冲区对象： 数据缓冲区，这是前的数据级别缓冲区中的编辑发生，而 visual 缓冲区，这是缓冲区，则的编辑缓冲区文本视图中显示。  
  
 会基于附加到基础的文本缓冲区，分类器设置格式和使用的修饰提供程序附加到文本视图本身修饰的文本。  
  
#### <a name="the-text-view-coordinate-system"></a>文本视图坐标系统  
 文本视图坐标系统指定的文本视图中的位置。 此坐标系中的 x 值 0.0 对应于正在显示的文本的左边缘和对应于正在显示的文本的上边缘的 y 值 0.0。增加了从左到右的 x 坐标和 y 坐标增加从顶部到底部。  
  
 视区 （文本窗口中可见的文本的一部分） 不能是相同的方式中水平滚动如垂直滚动。 视区是通过更改其左的坐标，使这方面的绘图图面的移动水平滚动。 但是，视区可被滚动垂直仅通过更改呈现的文本，这会导致<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>引发事件。  
  
 坐标系统中的距离对应于逻辑像素为单位。 如果未进行缩放变换的显示文本呈现图面，则文本呈现坐标系统中的一个单元对应于上显示的一个像素。  
  
#### <a name="margins"></a>边距  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>接口表示边距，并启用控件的边距和其大小的可见性。 有四个预定义的边距，也不能名为"Top"、"左"、"右侧"和"底部"附加到顶部、 底部、 左侧或右边缘的视图。 这些边距是的容器可以在其中放置其他边距重叠。 接口定义返回边距的大小和边距的可见性的方法。 边距是提供有关它们所连接的文本视图的其他信息的可视元素。 例如，行号边距显示文本视图行的号。 标志符号边距显示 UI 元素。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>接口处理的创建和放置的边距。 可以与其他边距重叠订购边距。 优先级较高的边距位于更靠近到文本视图。 例如，如果有两个左边的距、 边距 A 和边距 B，并且边距 B 有优先级低于边距 A，B 边距将出现边距 A.左侧  
  
#### <a name="the-text-view-host"></a>文本视图主机  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>接口包含文本视图和任何邻接修饰附带的视图，例如，滚动条。 文本视图主机还包含附加到视图的边框的边距。  
  
#### <a name="formatted-text"></a>格式化的文本  
 在文本视图中显示的文本组成<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>对象。 每个文本视图行对应于一行文本视图中的文本。 基础的文本缓冲区中的长行可以将部分遮盖 （如果未启用的自动换行），或者已被分成多个文本视图行。 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>接口包含方法和属性为坐标和字符，之间的映射和可能与行关联的修饰。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>通过使用创建对象<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>接口。 如果你只是担心当前视图中显示的文本，则可以忽略格式设置的源。 如果你感兴趣的不是文本格式显示在视图中 （例如，若要支持多格式文本剪切并粘贴），则可以使用<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>来设置文本格式的文本缓冲区中。  
  
 文本视图格式一个<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>一次。  
  
## <a name="editor-features"></a>编辑器功能  
 编辑器的功能，以便独立于其实现的功能定义的设计。 编辑器包括以下功能：  
  
-   标记和分类器  
  
-   修饰  
  
-   投影  
  
-   大纲显示  
  
-   鼠标和键绑定  
  
-   操作和基元  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a>标记和分类器  
 标记是与文本范围的关联的标记。 它们可以显示不同的方式，例如，通过使用文本着色、 下划线、 图形或弹出窗口。 分类器是标记的一种类型。  
  
 其他类型的标记是<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>的文本突出显示，<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>的大纲显示，和<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>编译错误。  
  
#### <a name="classification-types"></a>分类类型  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>接口表示等价类，这是一种抽象文本的类别。 分类类型可以多个-继承自其他分类类型。 例如，编程语言分类可能包括"关键字"、"注释"和"标识符"全都从"代码"继承。 自然语言分类类型可能包括"名词"、"谓词"和"形容词"，它们都继承自"自然语言"。  
  
#### <a name="classifications"></a>分类  
 分类通常是通过一段文本的特定分类类型的实例。 A<xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>用于表示一个分类。 可以将分类跨度看作适用于特定的一段文本，通知此文本范围的属于特定分类类型系统的标签。  
  
#### <a name="classifiers"></a>分类器  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>是一种将文本分解成一组分类的机制。 必须为特定的内容类型定义并为特定的文本缓冲区实例化分类器。 客户端必须实现<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>参与文本分类。  
  
#### <a name="classifier-aggregators"></a>分类器聚合器  
 分类器聚合器是一种机制，它为一个文本缓冲区的所有分类器将合并成只需一套分类。 例如，C# 分类器和一个英语语言的分类器可以创建分类通过 C# 文件中的注释。 请考虑此注释：  
  
```  
// This method produces a classifier  
```  
  
 C# 分类器可能标记为一个注释，整个范围和英语语言分类器可能分类"生成"为"谓词"和"方法"作为"名词"。 聚合器生成一组非重叠的分类，和的集的类型基于所有的参与意见。  
  
 分类器聚合器也是分类器，因为它将文本分解成一组分类。 有没有重叠的分类和分类进行排序，还可以确保分类器聚合器。 单个分类器都是免费若要按任何顺序返回任何分类，但重叠以任何方式。  
  
#### <a name="classification-formatting-and-text-coloring"></a>分类格式设置和文本颜色  
 文本格式设置是功能的基于文本分类的示例。 文本视图层使用它来确定应用程序中的文本的显示。 文本格式设置区域是依赖于 WPF 中，但分类的逻辑定义不是。  
  
 分类格式是一套格式设置特定分类类型的属性。 这些格式继承的父级的分类类型的格式。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>是从分类类型映射到一组的格式设置属性的文本。 在编辑器中的格式映射实现处理分类格式的所有的导出。  
  
###  <a name="adornments"></a>修饰  
 修饰是与的字体和颜色的文本视图中的字符不直接相关的图形效果。 例如，用于标记在许多编程语言的非编译代码，红色波形曲线下划线嵌入的修饰，同时工具提示弹出修饰。 修饰派生自<xref:System.Windows.UIElement>和实现<xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 两种特殊类型的修饰标记<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>，对于占据相同的空间视图中的文本的修饰和<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>，为波形曲线下划线。  
  
 嵌入的修饰是构成格式化的文本视图的一部分的图形。 其组织在不同的 Z 顺序层。 有三个内置的层，，如下所示： 文本、 插入符号和所选内容。 但是，开发人员可以定义多个层，并将它们放在相对于其他的顺序。 嵌入修饰的三类是相对于文本的修饰 （其中移动时移动文本，并删除时删除的文本）、 视图相对修饰 （它们具有如何处理非文本视图部分） 和所有者控制修饰 (开发人员必须管理它们的位置）。  
  
 弹出修饰是在文本视图，例如，工具提示的上一个小窗口中显示的图形。  
  
###  <a name="projection"></a>投影  
 投影是一种技术用于构造一种不同的不实际存储文本，而改为将合并来自其他文本缓冲区的文本的文本缓冲区。 例如，若要串联两个其他缓冲区中的文本，并显示结果，就像它是一个缓冲区中或隐藏的一个缓冲区中的文本部分，则可以使用投影缓冲区。 投影缓冲区可以充当另一个投影缓冲区的源缓冲区。 可以构造的一组通过投影相关的缓冲区进行不同的方式排列文本。 (也称为是这样一组*缓冲区关系图*。)Visual Studio 文本大纲显示功能的实施方式使用投影缓冲区以隐藏折叠的文本，并且 Visual Studio 编辑器中的用于 ASP.NET 页使用投影来支持嵌入的语言，如 Visual Basic 和 C#。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>通过创建<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>。 投影缓冲区由的有序<xref:Microsoft.VisualStudio.Text.ITrackingSpan>对象称为*源范围*。 这些范围的内容显示为字符序列。 从中绘制源范围的文本缓冲区名为*源缓冲区*。 投影缓冲区的客户端不需要注意，不同于普通文本缓冲区。  
  
 投影缓冲区侦听对源缓冲区的文本更改事件。 当源中的文本范围发生了更改时，投影缓冲区将更改的文本坐标映射到其自己的坐标，并引发相应的文本更改事件。 例如，考虑具有这些内容的源缓冲区 A 和 B:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 如果投影缓冲区 P 格式从这两个文本范围，具有所有缓冲区与另一个具有所有缓冲区 B，P 具有以下内容：  
  
```  
P: ABCDEvwxyz  
```  
  
 如果子字符串`xy`缓冲区 P 引发事件，该值指示已删除位置 7 和 8 个字符，然后从缓冲区 B，删除。  
  
 此外可以直接编辑投影缓冲区。 它将传播到合适的源缓冲区的编辑。 例如，如果字符串插入到缓冲区 P 位于 6 （字符"v"的原始位置），则插入会传播到缓冲区 B 中的位置 1。  
  
 有贡献投影缓冲区的源范围的限制。 源范围不能重叠;投影缓冲区中的位置不能映射到在任何源缓冲区中的多个位置，并且源缓冲区中的位置不能映射到投影缓冲区中的多个位置。 源缓冲区关系中不允许进行任何迂回情况发生。  
  
 源的一套缓冲投影缓冲区更改和源的一套跨更改时，将引发事件。  
  
 省略缓冲区是一种特殊的投影缓冲区。 它主要用于以大纲方式显示和展开以及折叠的文本块的操作。 省略缓冲区基于只有一个源缓冲区，并省略缓冲区中的范围都必须有序相同按照它们进行排序的源缓冲区中。  
  
##### <a name="the-buffer-graph"></a>缓冲区关系图  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>接口使跨投影缓冲区的图形映射。 定向非循环图形，类似于由语言编译器生成的抽象语法树中收集所有的文本缓冲区和投影缓冲区。 由顶层的缓冲区，它可以是任何文本缓冲区定义关系图。 从顶部到在源缓冲区中，点缓冲区中点或一组源缓冲区中的范围顶部缓冲区中的范围，则可以将映射缓冲区关系图。 同样，它可以映射点或源缓冲区中跨越到顶层缓冲区中的点。 缓冲区关系图通过使用创建<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>。  
  
##### <a name="events-and-projection-buffers"></a>事件和投影缓冲区  
 投影缓冲区修改时，修改从发送投影缓冲区依赖于它的缓冲区。 所有缓冲区被都修改后，会引发缓冲区更改事件，从最深的缓冲区。  
  
###  <a name="outlining"></a>大纲显示  
 以大纲方式显示为展开或折叠不同的文本视图中的文本块的能力。 以大纲方式显示被定义为一种类型的<xref:Microsoft.VisualStudio.Text.Tagging.ITag>中的相同方式定义修饰。 A<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>是一个标记，定义要展开或折叠的文本区域。 若要使用大纲显示，必须导入<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>获取<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>。 大纲显示管理器枚举，折叠，且将扩展的不同块，表示为<xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>对象，并相应地引发事件。  
  
###  <a name="mousebindings"></a>鼠标绑定  
 鼠标绑定链接鼠标移动到不同的命令。 通过定义鼠标绑定<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>，键绑定使用定义的和<xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>。 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>自动实例化的所有绑定，并将它们连接到视图中的鼠标事件。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>接口包含预进程和后续处理的事件处理程序不同的鼠标事件。 到事件中的一个的句柄，您可以重写中的方法的一些<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>。  
  
###  <a name="editoroperations"></a>编辑器操作  
 编辑器操作可以用于自动执行与编辑器中的，用于脚本编写或其他目的的交互。 你可以导入<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>上访问操作到给定<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 然后可以使用这些对象以修改所选内容、 滚动视图，或将插入符号移动到视图的不同部分。  
  
###  <a name="intellisense"></a>IntelliSense  
 IntelliSense 支持语句完成、 签名帮助 （也称为参数信息）、 快速信息和电灯泡。  
  
 语句结束提供的方法名称、 XML 元素和其他编码或标记元素的潜在完整内容的弹出列表。 一般情况下，用户手势调用完成会话。 会话显示的潜在完成列表和用户可以选择一个或关闭该列表。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>负责创建和触发<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>计算<xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet>会话完成项。  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)   
 [编辑器导入](../extensibility/editor-imports.md)