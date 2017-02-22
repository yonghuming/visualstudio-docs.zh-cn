---
title: "在编辑器内 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，新的体系结构"
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 31
caps.handback.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
---
# 在编辑器内
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

编辑器由组成的大量不同的子系统，旨在使编辑器文本模型单独从文本视图和用户界面。  
  
 下列各节介绍编辑器中的不同方面︰  
  
-   [子系统概述](../extensibility/inside-the-editor.md#overview)  
  
-   [文本模型](../extensibility/inside-the-editor.md#textmodel)  
  
-   [在文本视图](../extensibility/inside-the-editor.md#textview)  
  
 下列各节介绍编辑器的功能︰  
  
-   [标记和分类器](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [修饰](../extensibility/inside-the-editor.md#adornments)  
  
-   [投影](../extensibility/inside-the-editor.md#projection)  
  
-   [大纲显示](../extensibility/inside-the-editor.md#outlining)  
  
-   [鼠标绑定](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [编辑器操作](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> 子系统概述  
  
### 文本模型子系统  
 文本模型子系统负责表示文本并启用其操作。 文本模型子系统所包含 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 接口，它描述了编辑器中要显示的字符序列。 此文本可以修改、 跟踪和其他操作在很多方面。 文本模型还提供用于以下几个方面的类型︰  
  
-   一种服务，它使文本相关联的文件，并管理在读取和写入这些文件系统。  
  
-   一种差异服务发现的对象的两个序列之间的最小差异。  
  
-   一个系统，用于描述方面的其他缓冲区中的文本子集缓冲区中的文本。  
  
 文本模型子系统是免费的用户界面 \(UI\) 概念。 例如，概不负责文本格式或文本布局了，并且还可能与文本相关联的可视修饰一无所知。  
  
 Microsoft.VisualStudio.Text.Data.dll 和 Microsoft.VisualStudio.CoreUtilitiy.dll，仅依赖于.NET Framework 基类库和 Managed Extensibility Framework \(MEF\) 中包含的文本模型子系统的公共类型。  
  
### 文本视图子系统  
 文本视图子系统负责进行格式设置和显示文本。 该子系统中的类型分为两个图层，具体取决于是否类型依赖于 Windows Presentation Foundation \(WPF\)。 最重要的类型为 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 和 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, ，它控制的要显示的文本行集和还插入符号、 所选内容，以及用于通过使用 WPF UI 元素装饰文本的功能。 该子系统还提供了文本周围的边距的显示区域。 这些边距可加以扩展，并且可以包含不同类型的内容和视觉效果。 边距的示例包括行号显示和滚动条。  
  
 Microsoft.VisualStudio.Text.UI.dll 和 Microsoft.VisualStudio.Text.UI.Wpf.dll 中包含的文本视图子系统的公共类型。 第一个程序集包含独立于平台的元素，而第二个包含特定于 WPF 的元素。  
  
### 分类子系统  
 分类子系统是负责确定用于文本的字体属性。 分类器将文本分成不同的类，例如，"关键字"或"注释"。 分类格式映射与这些类实际字体属性，例如，"蓝色 Consolas 10pt"。 在设置格式和呈现文本时，文本视图使用此信息。 标记，在本主题稍后部分详细说明这使得能够将数据的文本范围与相关联。  
  
 分类子系统的公共类型都包含在 Microsoft.VisualStudio.Text.Logic.dll，并且它们与分类中，包含在 Microsoft.VisualStudio.Text.UI.Wpf.dll 的可视方面进行交互。  
  
### 操作子系统  
 操作子系统定义编辑器行为。 它提供了 Visual Studio 编辑器命令的实现和撤消系统。  
  
## 仔细地看文本模型和文本视图  
  
###  <a name="textmodel"></a> 文本模型  
 文本模型子系统包括不同类型的文本的分组。 其中包括文本缓冲区、 文本快照和文本段。  
  
#### 文本缓冲区和文本快照  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 接口表示一连串的使用 utf\-16，是由使用的编码进行编码的 Unicode 字符 `String` .NET Framework 中的类型。 文本缓冲区可保留为文件系统文档，但这不是必需。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 用于创建一个空文本缓冲区或从一个字符串，或初始化文本缓冲区 <xref:System.IO.TextReader>。 文本缓冲区可以保存到文件系统作为 <xref:Microsoft.VisualStudio.Text.ITextDocument>。  
  
 文本缓冲区可以编辑的任何线程，直到某个线程通过调用将获得文本缓冲区的所有权 <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>。 之后，只有该线程可以执行编辑操作。  
  
 文本缓冲区可在其生存期内经历许多版本。 新版本会生成每次编辑缓冲区，并将不可变 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 表示该版本的缓冲区的内容。 由于文本快照是不可变的可以访问而没有限制的任何线程上的文本快照，即使它表示的文本缓冲区不断更改。  
  
#### 文本快照和文本快照行  
 作为一系列字符或一系列行，您可以查看文本快照的内容。 字符数和行进行都索引从零开始。 一个空文本快照包含零个字符和一个空的行。 通过任何有效的 Unicode 换行字符序列，或通过的开头或结尾的缓冲区，分隔行。 换行字符显式表示文本快照中，并非所有需要是相同的文本快照中的换行。  
  
> [!NOTE]
>  有关在 Visual Studio 编辑器中的换行字符的详细信息，请参阅 [编码和换行符](../ide/encodings-and-line-breaks.md)。  
  
 文本行都由 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 对象，可以从特定的行号或特定的字符位置的文本快照中获得。  
  
#### SnapshotPoints、 SnapshotSpans 和 NormalizedSnapshotSpanCollections  
 一个 <xref:Microsoft.VisualStudio.Text.SnapshotPoint> 表示在快照中的字符位置。 位置被保证介于零和快照的长度。 一个 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 表示在快照中的文本范围。 保证其结束位置介于零和快照的长度。<xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> 包含一套 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 来自同一个快照的对象。  
  
#### 范围和 NormalizedSpanCollections  
 一个 <xref:Microsoft.VisualStudio.Text.Span> 表示可以应用于文本快照中的文本范围的间隔。 快照位置是从零开始，，因此范围就可以开始的任何位置包括零。`End` 的一段的属性是否等于之和其 `Start` 属性并将其 `Length` 属性。 一个 `Span` 不包括字符按索引的 `End` 属性。 例如，具有的起始范围 \= 5 且长度 \= 3 已结束 \= 8，它包括 5、 6 和 7 的位置处的字符。 在这段的表示法是 5..8）。  
  
 这两个范围相交如果它们具有任何共同的位置，其中包括的结束位置。 因此的交集 \[3, 5\) 和 \[2, 7\) 是 \[3, 5\) 和的交集 \[3, 5\) 和 \[5, 7\) 是 \[5，5）。 \(请注意，\[5，5\) 是空的范围。\)  
  
 如果它们具有共同的位置，除结束位置之外，这两个范围重叠。 空范围永远不会与任何其他范围重叠，且这两个范围的重叠永远不为空。  
  
 一个 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 是范围的范围的开始属性顺序的列表。 在列表中，将合并重叠或相邻的范围。 例如，对于指定的范围集 \[5..9\)，\[0..1\)，\[3..6\)，和 \[9..10\)，规范化的列表的范围是 \[0..1\)，\[3..10\)。  
  
#### ITextEdit、 TextVersion 和文本更改通知  
 可以通过更改文本缓冲区的内容 <xref:Microsoft.VisualStudio.Text.ITextEdit> 对象。 创建这样的对象 \(通过使用其中一个 `CreateEdit()` 方法 <xref:Microsoft.VisualStudio.Text.ITextBuffer>\) 启动文本事务，其中包含的文本编辑。 每个编辑是文本的某些范围的字符串缓冲区中的替代。 坐标和每个编辑内容相对于来表示缓冲区的快照事务启动时。<xref:Microsoft.VisualStudio.Text.ITextEdit> 对象调整受其他编辑操作在同一事务中编辑的坐标。  
  
 例如，考虑包含此字符串的文本缓冲区︰  
  
```  
abcdefghij  
```  
  
 应用事务，其中包含两个编辑、 替换在范围的一个编辑 \[2..4\) 使用的字符 `X` 和替换在范围的第二个编辑 \[6..9\) 使用的字符 `Y`。 结果是此缓冲区︰  
  
```  
abXefYj  
```  
  
 应用第一次编辑之前，第二个编辑的坐标都计算方面的事务，开头缓冲区的内容。  
  
 写入缓冲区的更改生效时 <xref:Microsoft.VisualStudio.Text.ITextEdit> 对象提交通过调用其 `Apply()` 方法。 如果没有至少一个非空编辑、 新 <xref:Microsoft.VisualStudio.Text.ITextVersion> 创建一个新 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 创建的且一个 `Changed` 引发事件。 每个文本版本具有不同文本快照。 文本快照之后执行编辑事务，表示文本缓冲区的完成状态，但文本版本描述仅从一个快照更改到下一步。 通常情况下，文本快照并打算使用一次，则丢弃，而文本版本必须仍保持活动状态一段时间。  
  
 文本版本包含 <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>。 此集合描述所做的更改，应用于快照时，将生成后续的快照。 每个 <xref:Microsoft.VisualStudio.Text.ITextChange> 集合中包含的更改、 被替换的字符串和替换字符串的字符位置。 被替换的字符串为空基本的插入操作，并替换字符串是空的某一基本的删除操作。 规范化的集合始终是 `null` 文本缓冲区的最新版本。  
  
 只有一个 <xref:Microsoft.VisualStudio.Text.ITextEdit> 对象可以在任何时候，实例的文本缓冲区，并且必须拥有文本缓冲区 （如果已声明所有权） 的线程上执行所有文本编辑。 可以通过调用放弃文本编辑其 `Cancel` 方法或其 `Dispose` 方法。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 此外提供了 `Insert()`, ，`Delete()`, ，和 `Replace()` 类似的方法上找到 <xref:Microsoft.VisualStudio.Text.ITextEdit> 接口。 这些调用不会有相同的效果创建 <xref:Microsoft.VisualStudio.Text.ITextEdit> 对象进行类似的调用，并将编辑。  
  
#### 跟踪点和跟踪范围  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> 表示文本缓冲区中的字符位置。 如果缓冲区进行编辑将导致要移动的字符的位置的方式，跟踪点会它随之切换。 例如，如果跟踪点是指在缓冲区中的位置 10，并且在该缓冲区的开头处都会插入五个字符，跟踪点然后指位置 15。 如果插入发生在精确地表示跟踪点的位置，其行为由其 <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, ，这可以是 `Positive` 或 `Negative`。 如果跟踪模式为正，跟踪点是指为现在位于插入; 末尾处的相同字符如果跟踪模式为负，跟踪点是指原始位置处的第一个插入字符。 如果删除由跟踪点位置处的字符，则跟踪点将切换到后面的已删除的范围的第一个字符。 例如，如果跟踪点指的是 5，位置处的字符，并且将删除位置 3 到 6 个字符，跟踪点是指位置 3 处的字符。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 表示字符而不是只需一个位置的范围。 其行为由其 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>。 如果范围跟踪模式，则 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，跟踪范围会增加，以使如果范围跟踪模式，则将在其边缘; 插入文本 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，跟踪范围未包含在其边缘处插入的文本。 但是，如果范围跟踪模式，则 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，插入将当前位置推送朝开头，并且如果 span 跟踪模式 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，插入将推送当前临近结束位置。  
  
 您可以获取文本缓冲区它们所属的任何快照跟踪点的位置或跟踪范围的跨度。 跟踪点和跟踪范围可以安全地从引用的任何线程。  
  
#### 内容类型  
 内容类型是内容的用于定义不同类型的机制。 内容类型可以是一个文件类型，例如"text"、"代码"或"binary"或"xml"、"vb"或"c\#"等技术类型。 例如，单词"using"是在 C\# 和 Visual Basic 中，但不是在其他编程语言的关键字。 因此，此关键字的定义会限制为"c\#"和"vb"内容类型。  
  
 内容类型用作筛选器修饰和编辑器的其他元素。 许多编辑器功能和扩展点定义的每个内容类型;例如，文本着色是不同的纯文本文件、 XML 文件和 Visual Basic 源代码文件。 文本缓冲区创建，并且可以更改文本缓冲区的内容类型时，通常会被分配一个内容类型。  
  
 内容类型可以多\-继承自其他内容类型。<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 允许您为给定的内容类型的父指定多个基类型。  
  
 开发人员可以定义自己的内容类型和使用注册 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>。 许多编辑器功能，可通过定义相对于特定的内容类型 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>。 例如，编辑器的边距、 修饰和鼠标处理程序可以定义，以便它们仅适用于显示特定内容类型的编辑器。  
  
###  <a name="textview"></a> 在文本视图  
 模型视图控制器 \(MVC\) 模式的视图部分定义文本视图中，视图中，如滚动条，并将插入符号的图形元素的格式设置。 Visual Studio 编辑器中的所有演示文稿元素基于 WPF。  
  
#### 文本视图  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 接口是独立于平台的表示形式的文本视图。 它主要用于文本文档显示在窗口中，但它还可用于其他用途，例如，在工具提示。  
  
 文本视图引用了不同类型的文本缓冲区。<xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> 属性是指 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> 指向这些三个不同的文本缓冲区对象︰ 数据缓冲区，而这是前的数据级别缓冲区中的编辑发生，并且 visual 缓冲区，而这是显示在文本视图中的缓冲区的编辑缓冲区。  
  
 文本的格式根据附加到的基础的文本缓冲区的分类器，并且通过使用附加到文本视图本身的修饰提供装饰。  
  
#### 文本查看坐标系统  
 文本视图坐标系指定文本视图中的位置。 在此坐标系统， x 值 0.0 对应于要显示的文本的左边缘与 y 值 0.0 对应于要显示的文本的上边缘。 x 协调从左到右，增加和 y 协调从上到下的增加。  
  
 视区 （文本窗口中可见的文本的一部分） 不能将相同的方式水平滚动如垂直滚动。 视区是通过更改其左边缘的坐标，使它移动方面的绘图图面的水平滚动。 但是，视区可以滚动垂直只能通过更改呈现的文本，这会导致 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 事件被引发。  
  
 坐标系统中的距离对应于逻辑像素为单位。 如果未进行缩放变换的显示文本呈现图面，则文本呈现坐标系中的一个单位的对应显示屏上的一个像素。  
  
#### 边距  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> 接口表示边距，并启用控件的边距和其大小的可见性。 有四个预定义的边距，也不能并且名为"Top"、"左"、"右"，"底部"附加到的顶部、 底部、 左侧或视图的右边缘。 这些边距是的容器，可以在其中放置其他边距重叠。 此接口定义返回边距的大小和边距的可见性的方法。 边距是可视元素，提供了有关它们所连接的文本视图的其他信息。 例如，行号边距中显示为文本视图的行号。 标志符号边距将显示用户界面元素。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 接口处理创建和放置的边距。 可以与其他边距重叠排序边距。 优先级较高的边距都位于更靠近到文本视图。 例如，如果有两个左边的距、 距 A 和距 B，而边距 B 具有比边距一个较低优先级，边距 B 将出现边距 A.左侧  
  
#### 文本视图宿主  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 接口包含的文本视图和伴随的视图中，例如，滚动条任何邻接修饰。 文本视图宿主还包含附加到该视图的边框的边距。  
  
#### 格式化的文本  
 在文本视图中显示的文本组成 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 对象。 每个文本视图行对应于一行文本视图中的文本。 在基础的文本缓冲区中的较长的行可以是部分遮盖 （如果未启用自动换行），或者已被分成多个文本视图行。<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 接口包含的方法和属性为坐标和字符之间的映射和可能与此线条关联的修饰。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 通过使用创建对象 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 接口。 如果您只需关心当前视图中显示的文本，则可以忽略格式的来源。 如果您有兴趣为不是文本的格式显示在视图中 （例如，支持多格式文本剪切和粘贴），则可以使用 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 来设置文本格式的文本缓冲区中。  
  
 文本视图格式之一 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 一次。  
  
## 编辑器功能  
 编辑器的功能设计用于使功能的定义是独立于其实现。 编辑器包括以下功能︰  
  
-   标记和分类器  
  
-   修饰  
  
-   投影  
  
-   大纲显示  
  
-   鼠标和键绑定  
  
-   操作和基元  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> 标记和分类器  
 标记是与文本范围的关联的标记。 它们可以展示以不同的方式，例如，通过使用文本着色、 下划线、 图形或弹出窗口。 分类器是标记的一种类型。  
  
 其他种类的标记为 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 的文本突出显示， <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 的大纲显示、 和 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 的编译错误。  
  
#### 分类类型  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 接口表示等价类，这是一个抽象的文本类别。 分类类型可以多\-继承从其他分类类型。 例如，编程语言分类可能包括"关键字"、"注释"和"标识符"，它们都继承自"代码"。 自然语言分类类型可能包括"名词"、"谓词"和"修饰"的它们都继承自"自然语言"。  
  
#### Classifications  
 分类通常是通过一段文本的特定分类类型的实例。 一个 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> 用于表示一种分类。 可以将分类跨度看作一个标签，该类适用于特定的一段文本，指示该文本范围的属于特定分类类型系统。  
  
#### 分类器  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 是一种将文本分成一组分类的机制。 必须为特定的内容类型定义并为特定的文本缓冲区实例化分类器。 客户端必须实现 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 参与文本分类。  
  
#### 分类器聚合器  
 分类器聚合函数是一种机制，它为一个文本缓冲区的分类器将合并成只需一套分类。 例如，C\# 分类器和一个英语语言的分类器可以创建分类通过 C\# 文件中的注释。 请考虑此注释︰  
  
```  
// This method produces a classifier  
```  
  
 C\# 分类器可能标记为一个注释，整个范围并将英语语言的分类器可能会对其分类"生成"作为"谓词"和"名词"的"方法"。 聚合函数生成一组非重叠分类，并集的类型取决于发布的所有内容。  
  
 分类器聚合函数也是分类器，因为它将文本分成一组分类。 存在任何重叠的分类和分类进行排序，还可以确保分类器聚合函数。 单个分类器都是免费以任何顺序返回任何一组分类，但以任何方式重叠。  
  
#### 分类格式设置和文本着色  
 文本格式设置是基于文本分类功能的一个示例。 文本视图层使用它来确定应用程序中的文本的显示。 文本格式设置区域是依赖于 WPF 中，但不是分类的逻辑定义。  
  
 分类格式是一套格式特定分类类型的属性。 这些格式会继承父代的分类类型的格式。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> 是从分类类型会映射为一组文本格式设置属性。 在编辑器中的格式映射实现处理所有导出项的分类格式。  
  
###  <a name="adornments"></a> 修饰  
 修饰是没有直接关系到的字体和颜色的文本视图中的字符的图形效果。 例如，用来标记在许多编程语言的非编译代码的红色波形曲线下划线是嵌入的修饰，而工具提示是弹出修饰。 修饰派生自 <xref:System.Windows.UIElement> 和实现 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 两种特殊类型的修饰标记 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, ，为占用相同的空间在视图中，文本的修饰和 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, ，为波浪线下划线。  
  
 嵌入的修饰是窗体中格式化的文本视图的一部分的图形。 它们都组织在不同的 Z\-顺序图层。 有三个内置层，如下所示︰ 文本、 插入符号和所选内容。 但是，开发人员可以定义多个层，并将其放在顺序对另一个。 嵌入的修饰的三类是相对于文本的修饰 （其中移动时移动文本，并删除时删除的文本）、 相对于视图的修饰 （它们具有与视图的非文本部分） 和所有者控制的修饰 （开发人员必须管理它们的位置）。  
  
 弹出修饰是在文本视图，例如，工具提示的上一个小型窗口中显示的图形。  
  
###  <a name="projection"></a> 投影  
 投影是一种技术用于构造一种不同的文本缓冲区不会实际存储文本，但改为组合其他文本缓冲区中的文本。 例如，来连接两个其他缓冲区中的文本，并显示结果，如同它只是一个缓冲区中或隐藏一个缓冲区中的文本的部分，则可以使用投影缓冲区。 投影缓冲区可以充当向另一个投影缓冲区的源缓冲区。 可以构造一组相关的投影的缓冲区，以采用许多不同的方式重新排列的文本。 \(这样一组也称为 *缓冲区关系图*。\) Visual Studio 文本大纲显示功能实现通过使用投影缓冲区来隐藏折叠的文本，并且 Visual Studio 编辑器中的用于 ASP.NET 页使用投影来支持嵌入的语言，如 Visual Basic 和 C\#。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> 通过创建 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>。 投影缓冲区都由的有序 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 对象被称为 *源范围*。 这些范围的内容显示为字符序列。 从中绘制源范围的文本缓冲区被命名为 *源缓冲区*。 投影缓冲区的客户端不需要注意它不同于普通文本缓冲区。  
  
 投影缓冲区侦听对源缓冲区的文本更改事件。 当源中的文本范围发生了更改时，投影缓冲区将已更改的文本坐标映射到其自己的坐标，并引发适当的文本更改事件。 例如，考虑具有这些内容的源缓冲区 A 和 B:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 如果从这两个文本范围的所有缓冲区 A，将另一个具有所有缓冲区 B，形成投影缓冲区 P P 具有以下内容︰  
  
```  
P: ABCDEvwxyz  
```  
  
 如果子字符串 `xy` 缓冲区 P 引发一个事件，指示已删除位置 7 和 8 个字符，然后从缓冲区 B，已删除。  
  
 此外可以直接编辑投影缓冲区。 它会将传播到适当的源缓冲区的编辑。 例如，如果一个字符串插入到缓冲区 P 位置 6 （"v"字符的原始位置），插入传播到缓冲区 B 中的位置 1。  
  
 有一些限制，构成投影缓冲区的源范围。 源范围不能重叠。投影缓冲区中的位置不能映射到多个位置中任何源缓冲区，并在源缓冲区的位置不能映射到投影缓冲区中的多个位置。 源缓冲区关系在允许有没有迂回情况发生。  
  
 当投影缓冲区更改和源的一套跨更改时，放入缓冲区的一套源时，会引发事件。  
  
 省略缓冲区是一种特殊的投影缓冲区。 主要用于以大纲方式显示和操作，展开和折叠的文本块。 省略缓冲区基于只是一个源缓冲区，并省略缓冲区中的范围必须排列在相同按照它们在源缓冲区进行排序。  
  
##### 缓冲区关系图  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> 接口允许通过投影缓冲区的图形映射。 定向非循环图形，很像由语言编译器生成的抽象语法树中收集所有文本缓冲区和投影缓冲区。 可以是任何文本缓冲区的前缓冲区由定义关系图。 从点到点在源缓冲区中的顶层缓冲区中或从一组源缓冲区中的范围的顶部缓冲区中的范围，则可以将映射缓冲区关系图。 同样，可以映射一个点或源缓冲区的跨度到顶层缓冲区中的点。 缓冲区关系图通过使用创建 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>。  
  
##### 事件和投影缓冲区  
 修改投影缓冲区时，所做的修改是从投影缓冲区发送到依赖于它的缓冲区。 修改所有缓冲区之后，缓冲区引发更改事件，开头的最深的缓冲区。  
  
###  <a name="outlining"></a> 大纲显示  
 以大纲方式显示为展开或折叠不同的文本视图中的文本块的能力。 以大纲方式显示定义为一种类型的 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, 中的相同方式定义修饰。 一个 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 是一个标记，定义要展开或折叠的文本区域。 若要使用大纲显示，您必须导入 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> 获取 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>。 大纲显示管理器枚举，折叠，且扩展，表示为的不同块 <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> 对象，并相应地引发事件。  
  
###  <a name="mousebindings"></a> 鼠标绑定  
 鼠标绑定链接鼠标移动到不同的命令。 通过定义鼠标绑定 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, ，并使用由程序定义的键绑定 <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>。<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 自动实例化的所有绑定，并将它们连接到视图中的鼠标事件。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> 接口包含不同的鼠标事件预处理和后处理事件处理程序。 对其中一个事件句柄，您可以重写中的方法的一些 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>。  
  
###  <a name="editoroperations"></a> 编辑器操作  
 可以使用编辑器操作来自动执行与编辑器中的，用于编写脚本或其他目的进行交互。 您可以导入 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> 上访问操作到给定 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 然后可以使用这些对象可以修改所选内容、 滚动视图，或将插入符号移动到视图的不同部分。  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense 支持语句完成、 签名帮助 （也称为参数信息）、 快速信息和电灯泡。  
  
 语句结束提供潜在完成项的方法名称、 XML 元素，以及其他编码或标记元素的弹出列表。 一般情况下，用户手势时，调用完成会话。 潜在的完成列表将显示会话和用户可以选择一个或关闭该列表。<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> 负责创建和触发 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 计算 <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> 的会话的完成项目。  
  
## 请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)   
 [编辑器中导入](../extensibility/editor-imports.md)